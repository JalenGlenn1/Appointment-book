"""AppointmentBook.py

This is a program that implements an appointment book.
There are two types of events that can be recorded in anappointment book:
a personal appointment, and a meeting. Both types of events consist of a
contact (the name andtelephone number of a person), and the start time of
the event.  Events always begin on the hour, and last for onehour.
An appointment book is a collection of events.
Events can be added to the appointment book, and the list ofevents for a
given date can be displayed.

"""

from abc import ABC, abstractmethod

# A Time has attributes for a Date (month, day, year), and time (24hr clock).
class Time:
  def __init__(self, month: int, day: int, year: int, hour: int):
    self.month = month
    self.day = day
    self.year = year
    self.hour = hour

# ToString for Time. Displays the date and time in "mm/dd/yyyy at hh:00" format
  def __str__(self):
    return self.get_date() + " at " + str(self.hour) + ":00"

# Returns a string representation of the date associated with this time
  def get_date(self) -> str:
    return str(self.month) + '/' + str(self.day) + '/' + str(self.year)


# A Contact has attributes for a person’s name and telephone number.
class Contact:
  def __init__(self, name: str, number: str):
    self.name = name
    self.number = number

# returns the contact name 
  def get_name(self):
        return self.name

# returns the contact phone number
  def get_phone(self):
        return self.number

# ToString for Contact
  def __str__(self):
    return "The name of the contact is " + self.name + ", and their number is " + self.number + "."

# An Event has an attribute for a contact, and an attribute for the starting date/time of the event.
class Event(ABC):
  def __init__(self, contact: Contact, time: Time):
    self.contact = contact
    self.time = time
    
  def get_header(self):
    return str(self.contact) + '\nMeet On: ' + str(self.time) + '\n'

# The AppointmentBook class should maintain an attribute that stores the list of events.

class AppointmentBook:
  event_list = []

# add_event method attempts to add the given event to the appointment book. 
# The method should not add an event if the new event will conflict with an existing event in the appointment book. 
# If there is no conflict, the given event is added to the appointment book. 
# If there is a conflict, the method should return without adding the given event to the appointment book.
  def add_event(self, event: Event):
    if self.is_available(event.time):
      self.event_list.append(event)
    else:
      print("Time or date is conflicting")

# This method returns a list of Events for the given date.
  def get_events_for_date(self, time: Time) -> list:
    return [event for event in self.event_list if event.time.get_date() == time.get_date()]

# Helper method check to see if time and date is available
  def is_available(self, time: Time) -> bool:
    for event in self.event_list:
      if (str(event.time) == str(time)):
        return False
    return True

# A Meeting has an attribute that maintains the names of the attendees.
class Meeting(Event):
  def __init__(self, contact: Contact, time: Time, attendees: list):
    super().__init__(contact, time)
    self.attendees = attendees

# ToString for Meetings. Generic event information, followed by the number of attendees
  def __str__(self):
    return self.get_header() + 'Number of Attendees: ' + str(len(self.attendees)) + '\n\n'

# Getter for the list of attendees
  def get_attendees(self):
    return self.attendees

# Adds and attendee into the meeting
  def addAttendee(self, name: str):
    self.attendees.append(name)

# Adds a list of attendees into the meeting.
  def addAttendees(self, names: list):
    for name in names:
      addAttendee(name);


# An Appointment has an additional attribute specifying the type of the appointment (e.g., “doctor’s visit”).
class Appointment(Event):
  def __init__(self, contact: Contact, time: Time, kind: str):
    super().__init__(contact, time)
    self.kind = kind

# ToString for Appointment. Generic event information followed by the type of appointment
  def __str__(self):
    return self.get_header() + 'Type of Appointment: ' + self.kind + '\n\n'

# The get_type method define a getter for the type of appointment
  def get_type(self):
    return self.kind


# Functionality Test of AppointmentBook.

book = AppointmentBook()

a1 = 'Jake'
a2 = 'Steve'
a3 = 'Doe'
a4 = 'Drake'
a5 = 'Herb'
a6 = 'Dugg'
a7 = 'Baby'
a8 = 'Kawhi'
a9 = 'Kevin'

c1 = Contact('Jalen', '(336) 555-6077')
c2 = Contact('Jay', '(614) 555-6078')
c3 = Contact('Glenn', '(513) 555-5658')

ap1 = Appointment(c1, Time(1, 20, 2021, 9), 'Doctor')
ap2 = Appointment(c1, Time(1, 20, 2021, 11), 'Lunch')
ap3 = Appointment(c1, Time(1, 20, 2021, 16), 'Car Service')
ap4 = Appointment(c1, Time(1, 20, 2021, 17), 'Interview')
ap5 = Appointment(c3, Time(1, 23, 2021, 9),  'Doctor')
ap6 = Appointment(c3, Time(1, 23, 2021, 11), 'Lunch')
ap7 = Appointment(c2, Time(2, 20, 2021, 16), 'Car Service')
ap8 = Appointment(c3, Time(2, 20, 2021, 17), 'Interview')

m1 = Meeting(c2, Time(1, 20, 2021, 8), [a1, a2, a3])
m2 = Meeting(c3, Time(1, 23, 2021, 8), [a1, a8, a3])
m3 = Meeting(c3, Time(1, 23, 2021, 8), [a5])
m4 = Meeting(c1, Time(1, 20, 2021, 8), [a1, a7, a9])
m5 = Meeting(c2, Time(2, 20, 2021, 8), [a2, a6, a9, a8])
m6 = Meeting(c3, Time(2, 20, 2021, 8), [a3, a6])
m7 = Meeting(c2, Time(1, 20, 2021, 8), [a8, a7, a5]) 
m8 = Meeting(c2, Time(1, 20, 2021, 8), [a1, a2, a3, a4, a5])

book.add_event(ap1)
book.add_event(ap2)
book.add_event(ap3)
book.add_event(ap4)
book.add_event(ap5)
book.add_event(ap6)
book.add_event(ap7)
book.add_event(ap8)

book.add_event(m1)
book.add_event(m2)
book.add_event(m3)
book.add_event(m4)
book.add_event(m5)
book.add_event(m6)
book.add_event(m7)
book.add_event(m8)

print('\n')

time = Time(2, 20, 2021, 0)
feb_events = book.get_events_for_date(time)


for event in feb_events:
  print(str(event))
