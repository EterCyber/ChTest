### Overview

ChTest is a distributed task queue for testing Xiangqi engines. The main instance
for testing the Xiangqi engine [Chameleon](https://github.com/EterCyber/Chameleon) is at this web page http://chtest.org

Developers submit patches with new ideas and improvements, CPU contributors install a ChTest worker on their computers to play some chess games in the background to help the developers testing the patches.

The ChTest worker:
- automatically connects to the server to download a chess opening book, the [sylvan-cli](https://github.com/EterCyber/Sylvan) chess game manager and the Xiangqi engine sources (both for the current Chameleon and for the patch with the new idea). The sources will be compiled according to the type of the worker platform.
- starts a batch of games using sylvan-cli.
- uploads the games results on the server.

The ChTest server:
- manages the queue of the tests with customizable priorities.
- computes several probabilistic values from the game results sent by the workers.
- updates and publishes the results of ongoing tests.
- knows how to stop tests when they are statistically significant and publishes the final tests results.
