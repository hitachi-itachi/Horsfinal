# Task:
The Merlion Hotel has more than 500 rooms in five different configurations – Deluxe Room,
Premier Room, Family Room, Junior Suite and Grand Suite. From time to time, the hotel
may change its room configurations to cater to changing needs of guests. The hotel has
various amenities to cater to the needs of guests, but these would be managed with a different
information system.
IS2103 – Enterprise Systems Server-side Design and Development
Tan Wee Kek, tanwk@comp.nus.edu.sg 2
The new system mainly manages the various room types as well as the room inventory. Each
room is numbered using a combination of a two-digit floor number and a two-digit sequence
number for that floor, e.g., Room 2015 would refer to the fifteenth room on floor twenty.
A room is available for allocation to a particular guest reservation if the room status is
available and has not been allocated to another guest reservation for the entire duration of the
current reservation. This business rule is important as the guests cannot be asked to change
room in the middle of their stay. Thus, the system needs to ensure that there is sufficient
room inventory to fulfil a new reservation before accepting it. In the event of overbooking for
a particular room type, the guests can be upgraded to the next higher available room type at
no additional cost.
In other words, when a new reservation request is received, the system does not need to
allocate a hotel room before confirming the reservation. The system only needs to ensure that
the hotel has sufficient room inventory to fulfil the new reservation. Allocation of hotel
rooms to guest reservations is done as a daily batch job at 2 am in the morning. If the system
encounters any errors during the room allocation process, an exception report would be
generated. The duty manager will need to check the exception report in the morning to
resolve the errors.
The standard check-out time is 12 noon on the day of departure and the standard check-in
time is 2 pm on the day of arrival. The housekeeping department will typically perform
cleaning between 12 noon to 2 pm. Early check-in is possible only if the room that is
allocated to the guests is ready before 2 pm. Late check-out is possible only if the room has
not been allocated to guests on the day of departure.
Merlion Hotel adopts a four-tier pricing strategy for its room rates:
• Published Rate – This is the base rate per night for a room type that is offered to all
walk-in reservations regardless of the check-in date.
• Normal Rate – This is the normal rate per night for a room type that is offered to
online reservation via HoRS, including external partners. This is the default rate per
night for any room type offered to all online reservations (own and partner).
• Peak Rate – This is the peak rate per night for a room type that is offered to all online
reservations (own and partner) via HoRS, including external partners, during
predefined peak seasons.
• Promotion Rate – This is the discounted rate per night for a room type that is offered
to all online reservations (own and partner) via HoRS, including to external partners,
during predefined promotional periods.
The total reservation fee payable by the guest for a reservation is calculated by summing the
prevailing rate per night of each night of stay for the entire duration of stay. For example, if a
guest books a Deluxe Room for 3 nights, the reservation fee will be the sum of first day’s rate
per night, second day’s rate per night and third day’s rate per night. If either peak rate or
promotion rate is defined for a particular room type on a particular date, it will take
precedence over the normal rate. If both peak rate and promotion rate are defined for a
particular room type on a particular date, the promotion rate will take precedence.
