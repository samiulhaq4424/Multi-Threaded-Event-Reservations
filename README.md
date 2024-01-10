# Multi-Threaded Event Reservations
## Multi-Threaded Event-Reservation System using pthread API

This project demonstrates the design and implementation of a multi-threaded event-reservation system for Nehru Centre using the pthread API. The reservation system efficiently handles inquiries, bookings, and cancellations for a set of events held in an auditorium. The implementation ensures data consistency, handles mutual exclusion, and manages concurrent access to the reservation database.

### Project Overview

The project involves creating a simulation of the event-reservation system with the following features:

- **Event Information:** The main thread initializes a list of events, each with a specific capacity of available seats.

- **Concurrent Queries:** Multiple worker threads run concurrently, generating random queries of three types: inquiring available seats, booking tickets, and canceling tickets.

- **Concurrency Control:** The system enforces a maximum limit on active queries (MAX) at any given time. Excess queries must wait until some queries complete. Condition variables are used to manage this restriction.

- **Mutual Exclusion:** To maintain data consistency, different threads accessing the same event use mutex locks for mutual exclusion. A shared table is maintained to track the active queries for each event.

- **Query Execution:** Worker threads execute queries, populate the shared table, perform bookings, and handle cancellations. Successful queries remove entries from the shared table.

- **Simulation Timing:** Threads introduce random delays to simulate real-world conditions between queries and during query execution.

- **Shutdown Handling:** After running for a specified time (T), all worker threads exit, and the master thread prints the current reservation status for all events before shutting down.

### Key Implementation Steps

1. **Event Initialization:** The main thread initializes the event list with their respective capacities.

2. **Thread Creation:** The main thread creates multiple worker threads (s threads) that simulate concurrent interactions.

3. **Query Generation:** Worker threads generate random queries (inquire, book, or cancel) and perform actions based on query type.

4. **Concurrency Management:** The MAX active queries restriction is enforced using condition variables, blocking excess queries until active queries complete.

5. **Mutual Exclusion:** Mutex locks ensure that only one thread at a time accesses or modifies event reservation data.

6. **Shared Table:** A shared table maintains active query information for events. Threads populate and remove entries based on query status.

7. **Query Execution:** Threads execute queries, update shared table entries, perform bookings, and handle cancellations.

8. **Simulation Timing:** Threads introduce random sleep intervals between queries and during query execution.

9. **Shutdown:** After running for time T, worker threads exit, and the master thread prints the final reservation status.

### How to Run

1. Compile the program using a C/C++ compiler that supports pthreads.
2. Execute the compiled binary.
3. Observe the simulation and the reservation system's behavior with diagnostic messages and final event reservation status.

### Parameters

- e: Number of events (e.g., 100)
- c: Auditorium capacity (e.g., 500)
- k: Number of tickets booked (random between 5 and 10)
- s: Number of worker threads (e.g., 20)
- MAX: Maximum concurrent active queries (e.g., 5)
- T: Total running time (1 - 10 minutes)


## Testing

- Thoroughly test the system with various configurations and scenarios.
- Test cases should cover different query types, concurrency levels, and edge cases.
- Validate that the system handles mutual exclusion, concurrency control, and query correctness.

## Results

- After running for the specified time (T), the system shuts down.
- All worker threads terminate gracefully.
- The master thread prints the final reservation status for all events.

## Conclusion

This project demonstrates the successful implementation of a multi-threaded event-reservation system using the pthread API. The system efficiently handles various types of queries, ensures data consistency through mutual exclusion, and manages concurrency using mutex locks and condition variables. The simulation provides insights into the challenges of multi-threaded programming and offers a robust solution for a real-world reservation system.
