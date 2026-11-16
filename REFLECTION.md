1.  For every function you wrote (TODO 1 to 19), explain in your own words what it does and
      give its time complexity in terms of n, the number of scenes.

**TODO 1-5 (scene.h)**

TODO1: The scene constructor stores the scene's data and allocates the exact number of pointer slots for its choices. And like the many times we iterate through a scenes choices, since we know the max is 3, that constant upper bound makes the loop over just one scene's choices have a  bigO of O(1). So the functions time complexity is O(1).

TODO2: The destructor, it recursively deletes each child scene, then the array of choice pointers, then the scenes own data. The function's time complexity is O(n) because the worst case is deleting every single scene in the tree starting from the root.

TODO3: isEnding(). Returns true only when the scene has zero choices. Time complexity is O(1) because it only checks a variable and there is no looping.

TODO4: getChoice(). Checks  if the given index is valid, then returns the scene pointer at that index. This is grabbing the chosen child from the current scenes array of choices. Time complexity is O(1) because we are just accessing an element of an array with a known index.

TODO5: setChoice(). Checks if the given index is valud, then stores a given scene pointer into the slot of the index. Time complexity is O(1) as we are once again just working with a known index and doing checks and assignments without any need for looping.

**TODO 6-9**

TODO 6: countScenes(). A recursive function that counts the total number of scenes must visit every scene in the tree once to add to a counter. Time complexity is O(n).

TODO 7: countEndings(). Another recursive function that counts all the scenes that have zero choices (a.k.a endings). Time complexity is O(n) because ti has to visit every scen to know how many endings exist.

TODO 8: height(). Recursive functionfinds the longest path from current scene to an ending. Time complexity is O(n), it has to visit every child to compare every height of every path.

TODO 9: clear(). Deletes the root scene, using the scene destructor from TODO 2 gives a O(n) time complexity when deleting root because all of tree will be reached in the process. Then sets root pointer to nullptr.

**TODO 10-12 (LOADING)**

TODO 10: load(). Opens the story file, reads HP, then calls readScene() to construct the entire story tree before storing the root. Time complexity is O(n) because loading requires reading and constructing all n scenes.

TODO 11: readScene(). Recursive and reads a scenes information, creating its Moment and Scene objects. Then recursively builds the subtrees. reaching each subtree and construcitng each scene once gives time complexity O(n) for this function.

**TODO 12-13 (PLAYING)**

TODO 12: askChoice() prints for the players input of a choice between a scenes children, repeatedly. Checking a valid choice is only O(1) becuase are only 3 choices at most, but time complexity is O(n) where n is the number of input attempts the player makes since they can do so repeatedly.

TODO 13: play(). oh boy. This function moves through the story based on player choices and respectively updates their HP, loot, and inventory until they either die or reach an ending. The time complexity is O(n^2). that is our worst canse because the player can visit up to n scenes, and searching through the linked-list inventory takes O(n) time as the number of items increases.

**TODO 14-19 (ANALYZING)**

TODO 14: printStats(). easy O(n) time complexity. prints number of scenes, number of endings, and longest possible path using the very methods that do this in StoryTree. its O(n) because all three methods called are O(n).

TODO 15: printSpoilers(). A recursive search for all the endings through calling printEndings() with the root scene. Visits every scene from root and that gives us the tree-traversal time complexity of O(n). 

TODO 16: printEndings(). recursive function that has to go to every branch and print the path and text of every ending it finds. Time complexity is O(n) because it will visit every scene no matter how many endings there are, it has to find them all.

TODO 17: greedyRun(). Plays the story automatically and always chooses whatever chils has the highest immediate loot, it does not care about consequences or grandchildren. That one path it follows still gives us O(n) for the number of scenes depending on the story.

TODO 18: bestLoot(). This recursive function checks every possible branch... so O(n) time complexity. it checks all these and rejects all death paths, and out of all surviving routes it chooses who came back with the most loot. 

TODO 19: optimalRun(). Calls bestLoot from the root and prints the most profitable surviving path, or a message if no such path survives. The work coming from he bestLoot() call cost a O(n) time complexity for this function.

2. We allocate exactly numChoices slots because the text adventure is expected to only give the data for the number of choices it claims to have. Allocating extra space for slots that will never be filled takes up unneccesary memory. An ending holds a nullptr in choices_ because that is the default and we never reach the block in the constructor to assign anything else. The nullptr assignment also cleans up nice.


3. The Scene destructor starts by going into and through deleting all existing child scene pointers of the current scene. This deletion of these scene pointers recursively calls through those children until the whole tree is reached. Then, or if there are no children, it dynamically deletes the choices array. Finally it deletes the Data in the present Scene pointer, and this step is guaranteed to happen for every scene pointer it visits. It has to visit every node of the tree because a scene owns all of its children, grandchildren, and data.


5. bestLoot tries every path, but runs O(n) becuase it only visites every scene once though the recursive process. Every finished path ends at a leaf, and a tree cannot have more leaves than scenes, and the amount of work grows with the number of scenes which means the number of times the recursion runs grows  in O(n) time.


6. My game uses search() to check if an item is already in inventory, if not then addFront() is used to insert it. addFront is always O(1), but as the list grows search cost O(n) because to reach each node for comparison it must travel from the head node until it finds the target.


    
