2. Requirements:
You must create a multi-threaded program using the POSIX pthread API. You will be simulating some functionality of the power system on a spacecraft. Your program must update the battery's voltage, current and temperature readings constantly. We must also check these values to see that the values are within an expected range, and finally check to see if the power system as a whole is doing okay.
You should have at least three thread's in your program, all sharing a single resource that is the battery (in the form of the battery vector array).
First thread (every 30us):
This thread will be updating the operational values of the EPS board(electronic power system)
(EPS_CURRENT_VAL, EPS_VOLTAGE_VAL, EPS_TEMPERATURE_VAL)
using the given functions that will provide values for the board(see next section).
Second thread (every 3 seconds):
The job of this thread is to check the operational values of the EPS board againt the given expected values, and assign values to the state of each value
(EPS_CURRENT_STATE, EPS_VOLTAGE_STATE, EPS_TEMPERATURE_STATE).
This will be either NOMINAL, WARNING, or DANGER.
A value has the state:
NOMINAL if the reading is the SAFE value +/- warning_threshold,
WARNING if the reading is the SAFE value +/- danger_threshold,
DANGER if the value is outside SAFE +/- danger_threshold.
This thread should also print the values of each reading.
Third thread (also every 3 seconds):
This thread will be responsible for checking for the state of each reading on the EPS board, reporting bad states, and responding to them.
This thread will handle non-normal states thus:
If all values report nominal state, or strictly fewer than 2 values were in critical, or warning state, do nothing
If two or more states are in warning, and none in critical, report the bad statesto the terminal
If two or more states are non-nominal, and at least one of them is in a critical state, report the bad states and increment
EPS_ALERT value in the EPS battery vector to keep track of the number of such states.
If EPS_ALERT reaches 5, as in condition (c) was met 5 times, report the bad states, reset the EPS_ALERT counter, and cancel all threads execution for 10 seconds before beginning them again. (note: you can assume that the counter is initialized to 0 since it is part of the array that is declared globally)
Your implementation MUST make use of thread synchronization features (such as a mutex, or semaphore) to ensure that the shared space in memory (battery vector) is not accessed by two threads at once!