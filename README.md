# Group-Project

#Write a query to list out the names and the pay rate if pay rate is greater than the average pay rate of staff from Las Vegas. 

SELECT firstName, lastName, CONCAT(“$”, payRate)
FROM Staff
WHERE city = "Las Vegas" AND payRate > (SELECT AVG(payRate) FROM Staff);

#Write a query to display which ticket platform offered tickets under $30 from 2022 and list out ticket prices to those concerts and the venue names.

SELECT Ticket.ticketPlatform, CONCAT(“$”,Ticket.ticketCost), Concert.concertDate, Venue.venueName
FROM Ticket
JOIN Concert ON Concert.concertID = Ticket.concertID
JOIN Venue ON Venue.venueID = Concert.venueID
WHERE Ticket.ticketCost < 30
AND Concert.concertDate REGEXP "^2022";
