# Keyword-searching-for-Client-Server
A server for keyword searches on a text file and a client that specifies a keyword to server via requests.
The server uses shared memory segments and semaphores to communicate with clients(at most 10). When recieved a request server starts a thread that searches the requested keyword in the previously given txt file. Results are written into a shared memory buffer called *result queues*. To make a request clients first grab a *state queue* semaphore to find a index for result queues(if all state queues are occupied client terminates). After grabbing the index client makes a request to server with it's *result queue* index and keyword to be seeked. Then releases the semaphore. To start reading from it's *result queue* which is indicated by the index number that it grabbed previously. To read from *result queue* client grabs the related semaphore. After reading and printing it releases the semaphore. Termination signal for client is passed by server when request is complete. Developed for Linux with C.


NOTES:
After first compilation run server first with your arguments. Then, any number of clients can be executed.

If you want to re-run the server, make sure clear the comments starting from server.c line 253 to 265. Then, compile and run twice while those comments are cleared. This is for clean-up purposes, since server is not supposed to terminate, there is no need to do auto clean-up. Therefore, it needs to be done by hand for re-executing.

Group Members: Berat Biçer(@ https://github.com/benazus) Alper Şahıstan
