# RSA-Projects
Simple programs designed to implement an RSA method of encoding between two endusers.

Summary: RSA is cool and hard to break! Why not make it easy to encode things between people with a simple program to encode yourmessages?

Motivating mathematical exploit: For sufficiently large primes, factorization is very difficult. A user with access to 2 large primes can therefore create an essentially impentetrable number, and from it, importantly, find an m, the lcm of the two primes, which can be used in conjunction with a public r to decode any message desired. r can be made small enough so as to be impossible to associate with a specific m. User A seeking to message User B first obtains B's r and large product of primes, pq, which are publically available. A's message is converted into an integer, and then that int to the rth power is sent modulo pq. This number is highly safe because there are a number of messages which return the same number, but each is unique to a given r. Then, using a second algorithm, User B is able to find a "key" so to speak to decode the message by finding an inverse for r, mod m. Since m is only known to them, and hard to guess, this is a safe key.

Public use: For two interfacing users, user A pings for r and n = pq, which we allow to be intercepted, and then encodes and returns their message, which we also allow to be intercepted. User B then possesses m (in a secure place, ideally) and can compute the message locally, and return a message to user A in the same way, using a's r and n. Interceptors without either m will be unable to decipher the emssages, and the actual messages and m's are stored locally to prevent misuse.


Sketch of function: 
    -A user database system
    -a library of large primes
    -something to find a relatively prime number r
    -for 2 primes, and the associated m
    -a message encoder to translate some string message into a large number, 
      -provides a way of distinguishing between small words and broken up words
    -a formatter for received, deciphered messages which eliminates spaces with some intelligence
    -a powerful modular arithmetic calculator for large numbers and powers
      -factorizes exponents to more intelligently calculate products
      -also calculates r inverse mod m, using known algorithm
