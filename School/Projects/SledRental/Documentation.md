## Database diagram
![Database diagram](School/Projects/SledRental/Images/DBDiagram.png)

---
<div style="page-break-after: always;"></div>

## Reservation Input mask documentation
### Structure
![Reservation Input Mask](School/Projects/SledRental/Images/ReservationInputMask.png)
### Field types
1. `Date` field of type `DateTime`
2. `Start time stamp` field of type `DateTime` 
   > Only time is important here
3.  `End time stamp` field of type `DateTime` 
   > Only time is important here
4. `Sled Catagory``field of type 'Sled'
	> It is selected using the category and the ID of the sled.
### Validations
1. `Date` can't be empty.
2. `Start Time Stamp` can't be empty and should be earlier than `End Time Stamp`
3. `End Time Stamp` can't be empty and should be later than `Start Time Stamp`
4. `Sled Catagory` can't be empty
> Note: I didn't have enough time to check if the `sled` is available or not and to display only sleds that are available.
> Reason of the latency: I didn't understand the task correctly at first and had to invest some time correcting it.
> How I would do it if had more time: I would declare a new list of the sleds in the `Add Reservation` view and filter the list always to include all sleds that are available during the chosen time of the user.
---

### Tests 
> Day of test: 2023-01-27
#### Failing Tests
1. (13:00) Deleting the `Date` field will result the error message: `The Date field must be a date.`
2. (13:26) Setting the `End Time Stamp` to a time earlier or equal to `Start Time Stamp` will result the error message: `StartTimeStamp must be earlier than EndTimeStamp.`
### Success Tests
1. (13:31) Changing the `End Time Stamp` field to have a later time than `Start Time Stamp`
2. (13:31) Making sure `Date` Field is not empty
3. (13:31) Normally `Sled Catagory` Field can't be empty.
### Notes
1. Leaving the `Start Time Stamp` or the `End Time Stamp` empty will set the value to the Time the Input Mask was created, meaning it will work even if one of the fields are empty, but when both are empty the `End Time Stamp` will be equal to the `Start Time Stamp` resulting in an `StartTimeStamp must be earlier than EndTimeStamp.` Error message.
---
Mahmoud Zino <span style="display: block; text-align: right;">4APEC</span>


