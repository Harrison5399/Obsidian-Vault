# TODO
- Look up good react application design (code wise)

## Stack
**todo, need to run through what these things are actually going to do, add things like zod or prisma and how you are going to handle them to ensure continuity**
Next.js
- Front end
- Back end
NextAuth.js
- API auth
- JWT
UI
- https://fullcalendar.io/
	- Calendar
- https://ui.mantine.dev/
- https://ui.shadcn.com/
Postgres

DATABASE SCHEMA
---
**ALL TABLES SHOULD HAVE TIMESTAMPS (createdAt & updatedAt)**
**User**
- userId
	- uuid
	- primary key
- firstname
	- string
- lastname
	- string
- rootFolder
	- uuid
	- points to users base root folder that is created on user creation
- settings
	- uuid
	- points to users settings object that is created on user creation
	- *should this be a ref to a seperate table? Think about population in the api, what is standard, does it depend if your using a document db or a relational db*
	- *Should the seperate table contain a userId or is querying for just this settings id every time in the db an okay way to query?*

**Setting**
- settingId
	- uuid
	- primary key
- (misc. settings here that should be easily expanded and adapted in the api)
	- *possibly break these down into each of the apps modules?*

***What do the routes look like for searching, what if you want to get everything with a given tag? or what about just getting every calendar event with a specific tag, where is the best place for these routes to lay in the api and does this Tags table need changed?***
**Tag**
- tagId
	- uuid
	- primary key
- userId
	- uuid
	- secondary key, point to user
- color
	- best form to store color
- title
	- string
- desc
	- string

***Should Folder, file, and journal all be in the same table and its own thing, they are all going to have different fields, but they are all items (idk what to call them but file tree items, is there a better name). I think of it as an abstract table that has the ids and type and order, and then seperate folder, file, and journal tables?
How to handle folder tags, should they cascade down? If not I dont see the point of having the tags at all
Is this the best way to handle a file folder structure with custom file types like journal (in all ways but also thinking about the order field, does that need reworked) , what about parsing in and out custom file types like converting the journal to some md structured format or saving as some json
IDEA - have metadata field with json obj with order and new level field to track depth of where it is in folder/file structure***
**Folder**
- folderId
	- uuid
	- primary key
- type
	- string=folder
- order
	- int
- tags
	- array of tagIds

**File**
- fileId
	- uuid
	- primary key
- type
	- string = folder
- order
	- int
- data
	- *binary or whatever the best way to store files would be for selected db*
- size
	- float
- title
	- string
- tags
	- array of tagIds

***Should journals have tags and/or entries?***
**Journal**
- journalId
	- uuid
	- primary key
- type
	- string = folder
- order
	- int
- data
	- array of entryIds
- title
	- string
- tags
	- array of tagIds

***Is this the best way to handle entries?***
**Entry**
- entryId
	- uuid
	- primary key
- order
	- int
- title
	- string
- desc
	- string
- tags
	- array of tags
- content
	- string, this should accept md formated string, and it will be long most likely
	- *should this field name be changed to "data"*

***Should calendar event and calendar todo, (and possibly event DailyTrackerId) remain their seperate tables or do another abstract thing like possibly done for folder,file,journal, like having a calendar activity with a type=... and having a title, desc, date, tags? I want to keep consistency and scalability throughout the app. I do not like the name  for the tables
I did not account for reoccuring events, I am not sure how this should be implimented i need guidance, hopefully optimizing for ease of optimization of creating, modifying or editing some reoccuring event and all the other events changing, i think the optimization im thinking of is just having reoccuing events auto fill into actually created events into calendar events, but it may be best to have its own table, i do not know what is standard and most efficenent and opimized***
**CalendarEvent**
- eventId
	- uuid
	- primary key
- title
	- string
- desc
	- string
- date
	- date
- startTime
	- time
- endTime
	- time
- tags
	- array of tagIds

CalendarTodo
- todoId
	- uuid
	- primary key
- title
	- string
- desc
	- string
- date
	- date
- time
	- time
- tags
	- array of tagIds

***I find it difficult to find a good word to seperate calendar and dailyTracker, not sure what to call it
DailyTrackerEvent should be able to have some sort of journal entry attached to it, so like if you click on it, you should be ableto desctibe what you did during said thing tracked, or possibly attach other things for futrue modules like finance, or personal fitness, in that case would the entry table need an added tag to determine if it belongs to a journal or is a free entity, or what about just attaching it to some auto created journal for that day of the tracked event***
**DailyTrackerEvent**
- dailytrackerid
	- uuid
	- primary key
- title
	- string
- desc
	- string
- links
	- array of entryIds
- date
	- date
- startTime
	- time
- endTime
	- time
- tags
	- tagIds

*This is a type of a kind of module that i expect to create more of and when put together will make an app module, not sure where I am going to display habbits yet, but they will be some structure that can be displayed in a list or in a popup like dailytrackerevent and possbily as an entry to a journal, so journals should not have such restircted arrays to any kind of type module or i dont know what to call it, and habbit itself should have options/settings on creation*
**Habbit**
- habbitId
	- uuid
	- primary key
- title
	- string
- tags
	- tagIds
- order
	- orderId
- type
	- some specific strings, like incremental (kinda just like a number input in html)
	- *Im not sure everything that will be tracked here, I would like to come up with some more uses, think more than just habbits and what some user of this app could store here*



IDEAS
---
- tags can have timeline (ai?)
	- tracks progress of some goals that are being journaled
	- lives somewhere in folder/file system
- rename habbit and figure out types and how to handle these inputs and then do some sort of calculation to them (stored in some "calculated" timeline, habbits connected to timelines do calculation,, i dont like the name it needs to have some new name, need more examples of use, examples: zyn use (daily), how many times ive done the dished (weekly)
- what to call folder/file system, i also think that the idea of having custom "file" types like the journal is currently should be embrased, this system will be the main organization, so having something like a folder called habbits with habbits inside of them, or a folder for projects different projects, and each have their own ai timeline created,
	- so then the idea is to have a special thing for the journal of a given day, its entries should be parsed into some sort of specific tag or linked folder, meaning you just have to type (sequentially possibly, maybe not important, maybe to connect things to daily tracker?) into a journal, and each entry you make, maybe linked to a specific tag, or a given folder (im thinking maybe just tag but i dont know how to determine where to actually put it? maybe there should be something special with a tagged folder that you can make it so the progress of these things are tracked by month, things can also be linked from other modules like daily tacker, and calendar event todos, and other things like habits?), but like i was saying, these entries from these special journals are distributed to the entries tag?
		- what is a good name for these possibly tagged folder (also note they should not be limited to just these special files, but other content too like folders or whatever that are normal), and for these special journals

for a given day journal it has entries with tag or linked special file,
- if speical tag linked,
	- entry gets distributed to this special tags, current month (or whatever set interval, could be week), special file, and appended to the bottom of the journal entries for that special file, and it is given the title of the date, or this is somehow kept track in the metadata or something of this entry for later tracking
- if linked to special file
- no idea, brain hurts, cant get my head off of trying to do it with tags, tags are the connection between everything