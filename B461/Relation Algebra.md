#### Operations

| Symbol             | Operation         | SQL Command |
| ------------------ | ----------------- | ----------- |
| $\sigma$           | Select (columns)  | SELECT      |
| $\pi$              | Project (rows)    | WHERE       |
| $\cup$             | Set Union         | UNION       |
| $\cap$             | Set Intersect     | INTERSECT   |
| $-$                | Set Difference    | EXCEPT      |
| $\times$           | Cartesian Product |             |
| $\bowtie$          | Join              |             |
| $p$                | Rename            |             |
| $\leftarrow$       | Assignment        |             |
| $\delta$           | Distinct          |             |
| $\tau$             | Sort              |             |
| $\Sigma$           | Aggregation       |             |
| $\gamma$           | Grouping          |             |
| $\fullouterjoin$ ⟗ | Full Outer Join   |             |

#### Examples

**Location**

| ship          | planet  |
| ------------- | ------- |
| Enterprise    | Earth   |
| Enterprise II | Mars    |
| Yangtze       | Azeroth |
| Defiant       | Azeroth |

**Captains**

| firstName | lastName | rank | ship          |
| --------- | -------- | ---- | ------------- |
| James     | Kirk     | 4.0  | Enterprise    |
| Jean-Luc  | Picard   | 4.0  | Enterprise II |
| Benjamin  | Sisko    | 3.0  | Defiant       |
| Kathryn   | Janeway  | 4.0  | Voyager       |
| Nerys     | Kira     | 2.5  | Yangtze       |

**First Officers**

| firstName | lastName | rank | ship          |
| --------- | -------- | ---- | ------------- |
| Spock     | NULL     | 2.5  | Enterprise    |
| William   | Riker    | 2.5  | Enterprise II |
| Nerys     | Kira     | 2.5  | Defiant       |
| Chakotay  | NULL     | 3.0  | Voyager       |


**$\sigma _{\text{rank}=4.0}(\text{Captian})$**

| firstName | lastName | rank | ship          |
| --------- | -------- | ---- | ------------- |
| James     | Kirk     | 4.0  | Enterprise    |
| Jean-Luc  | Picard   | 4.0  | Enterprise II |
| Kathryn   | Janeway  | 4.0  | Voyager       |

**$\pi_{\text{firstName}}(\text{Captain})$**

| firstName |
| --------- |
| James     |
| Jean-Luc  |
| Benjamin  |
| Kathryn   |
| Nerys     |

**$\pi_{\text{firstName}}(\text{Captain}) \cup \pi_{\text{firstName}}(\text{First Officer})$**

|firstName|
|---|
|James|
|Jean-Luc|
|Benjamin|
|Kathryn|
|Nerys|
|Spock|
|William|
|Chakotay|

**$\pi_{\text{firstName}}(\text{Captain}) \cap \pi_{\text{firstName}}(\text{First Officer})$

|firstName|
|---|
|Nerys|

**$\pi_{\text{firstName}}(\text{Captain})-\pi_{\text{firstName}}(\text{First Officer})$**

| firstName |
| --------- |
| James     |
| Jean-Luc  |
| Benjamin  |
| Kathryn   |

**$\text{Captain} \times \text{First Officer}$**
Creates a large table with every captain paired with every first officer

**$\text{Captain} \bowtie \text{First Officer}$**

|firstName|lastName|rank|ship|firstName|lastName|rank|ship|
|---|---|---|---|---|---|---|---|
|James|Kirk|4.0|Enterprise|Spock|NULL|2.5|Enterprise|
|Jean-Luc|Picard|4.0|Enterprise II|William|Riker|2.5|Enterprise II|
|Benjamin|Sisko|3.0|Defiant|Nerys|Kira|2.5|Defiant|
|Kathryn|Janeway|4.0|Voyager|Chakotay|NULL|3.0|Voyager|


#### Query Plans







