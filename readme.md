# Cinema Ticket Booking

A small C# console application that demonstrates how arrays can be used to store and update cinema seat data.

## Purpose

The project models a cinema with 3 rows and 5 seats in each row. Each seat stores a text value:

- `Available` means the seat can be booked.
- `Booked` means the seat has already been selected.

The project is intended as an example of using a two-dimensional array to represent data in rows and columns.

## Concepts Demonstrated

### Two-dimensional arrays

`CinemaBooking` declares a two-dimensional string array:

```csharp
string[,] seats;
```

The array is created from the number of rows and columns passed to the constructor:

```csharp
seats = new string[rows, columns];
```

The first index represents a row and the second index represents a seat within that row. For example, `seats[0, 2]` is the third seat in the first row.

C# arrays use zero-based indexing, so the program subtracts 1 from the numbers entered by the user. The user sees rows and seats numbered from 1, while the array uses indexes from 0.

### Initialising array data

Nested `for` loops visit every position in the array and set its initial value to `Available`:

```csharp
for (int i = 0; i < rows; i++)
{
    for (int j = 0; j < columns; j++)
    {
        seats[i, j] = "Available";
    }
}
```

The outer loop moves through rows, and the inner loop moves through the seats in each row.

### Reading and updating array values

The current value of a seat is read with its row and seat indexes:

```csharp
if (seats[rowNo, seatNo] == "Available")
{
    seats[rowNo, seatNo] = "Booked";
}
```

This demonstrates how an array can be both queried and changed while the program is running.

### Classes, fields, and constructors

The `CinemaBooking` class groups the seat data and the operations that work with it. Its constructor receives the dimensions of the cinema, stores them in fields, and allocates the array.

The class provides methods for:

- Displaying the seat layout with `printCurrentSeatStatus()`.
- Booking a seat with `bookSeat()`.

### Input validation

Before accessing the array, the program checks that the selected row and seat are within the valid range. This prevents invalid indexes from being used and allows the program to report an invalid selection.

### Loops and repetition

The `Main` method uses a `while` loop so the user can continue booking seats until they enter something other than `yes`.

## Program Flow

1. Create a `CinemaBooking` object with 3 rows and 5 seats per row.
2. Fill every array position with `Available`.
3. Display the initial seat layout.
4. Ask the user for a row and seat number.
5. Check the selected indexes and current seat status.
6. Change the selected value to `Booked` when it is available.
7. Display the updated layout.
8. Repeat until the user chooses to stop.

## Running the Project

From the project directory, run:

```bash
dotnet run
```

The project targets .NET 9.0 and is defined in `Ticket_Booking.csproj`.

## Limitations

- Seat data is stored only in memory and is lost when the program exits.
- The program stores text values instead of a dedicated seat or booking type.
- Non-numeric input can cause an input conversion error.
- The cinema size is fixed by the values passed to the constructor in `Program.cs`.

These limitations leave room for future improvements, such as saving bookings to a file, using safer input parsing, or replacing the text values with an enum.
