# DB Fundamentals

## Good pratcies
1. Alwasy have your query bounded. <br/>
SELECT PID, QNT*PRICE FROM SALES            >> BAD (not bounded) <br/>
SELECT PID, QNT*PRICE FROM SALES WHERE ...  >> GOOD

## ACID

### Isolation
1. Read Phenomenas
   1. dirty read.
   2. Non-repeatable reads.
   3. Phantom reads.
   4. Lost updates.
2. Isolation levels.
3. 