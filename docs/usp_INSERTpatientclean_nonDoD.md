# usp_INSERTpatientclean_nonDoD
Inserts patients into patientclean_nonDoD.

ceg_admin.dbo.**usp_INSERTpatientclean_nonDoD**

Inserts Regular patients with no Date of Death recorded but who have a code indicating death (eg Patient Died, Died in Hospital etc) in their record or who are aged 100+years old. Excluding any of these patients who have a non-admin observation code recorded in the last 10 years.

```SQL
USE ceg_admin;
EXEC usp_INSERTpatientclean_nonDoD
```

### CTV3 deceased codes
code | term
- | -
XE2Hq | FP22-death
XM01Y | Patient Died
949.. | Patient died - to record place (& [place of death])
9491 | Patient died at home
9492 | Patient died in: [part 3 accom] or [part 4 accom]
9493 | Patient died in nursing home
9494 | Patient died in residential institution NOS
9495 | Patient died in hospital
9496 | Patient died in street
9497 | Patient died in public place NOS
9498 | Dead on arrival at hospital
9499 | Found dead at accident site
949Z. | Patient died in place NOS
Xa7nB | Found dead in bed
Xa9sg | Patient died during operation
Xaafy | Patient died in usual place of residence
Xabh7 | Died in ambulance
Xabkk | Patient died in hospice community lodge
Xac3V | Died in learning disability unit
Xac3W | Died in mental health unit
XaEK5 | Patient died in hospice
XaJ2g | Patient died in community hospital
XaJrK | Patient died in GP surgery
XaVwv | Patient died in care home
XE2IO | Patient died in part 3 accommodation
XE2TT | Patient died in part 4 accommodation
XE2IN | Cremation certification
XE2xp | Patient died - to record place
8HG.. | Died in hospital

### CTV3 Admin codes
code | term
- | -
Y0de6 | Textual Problem
 931.. | Lloyd George Folder
XaBHV | Lloyd George record status
XaAKo | Sending of medical records to health authority
Y237d | Additional SCR dataset uploaded under COPI Regulations
XaJHC | Email sent to outside agency
XabYo | Email received from third party