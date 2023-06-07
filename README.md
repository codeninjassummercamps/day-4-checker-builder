# Day 4 Checker Builder

```template
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
```

## Checker Builder

Try out what you've learned about loops and nesting by teaching the agent how to build a checker board pattern!

## Step 1

Some code has already been provided for you. Take a second to try to figure out what the provided code does.

## Step 2

You might have guessed already, but the provided code is going to help make sure the agent starts in the right place, faces the right direction, and holds the right blocks! Now let's get started coding!

## Step 3

Our goal is going to be to use the width and length variables to make a custom sized checker board. To make a square with side lengths of the width and length, we need 2 ``||loops.repeat||`` loops. Find them and add them inside of each other at the end of the chat command. Place the length variable in the first (outer) one and the width veriable in the second (inner) one.

```blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {

        }
    }
```

## Step 4

The code inside of the width loop will end up happening for every block in the square, so this will be where we actually place the blocks. But first, we need to know which block to place. Find the ``||agent.set active slot||`` block and the ``||agent.place||`` block. Then, find the ``||variables. color||`` block to put inside the number of the ``||agent.set active slot||`` block.

```blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {
            agent.setSlot(color)
            agent.place(FORWARD)
        }
    }
```

## Step 5

After placing the block, there are two more things to do to prepare for the next block. The agent needs to move to the next spot, and the agent needs to switch colors! First, grab a block from the agent section that will make the agent move a step right. Then, grab an ``||logic.if||`` from the logic section.

``` blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {
            agent.setSlot(color)
            agent.place(FORWARD)
            agent.move(RIGHT, 1)
            if(true){

            }
        }
    }
```

## Step 6

To switch colors, we first need to know what color we already have so we know which color to change to! In the condition of the if, add the equal sign from the logic section, then grab the ``||variables.color||`` variable and place it in the first slot of the equal. In the second slot of the equal, type the number 1.

``` blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {
            agent.setSlot(color)
            agent.place(FORWARD)
            agent.move(RIGHT, 1)
            if(color == 1){

            }
        }
    }
```

## Step 7

If the color was the first color, we want it to be the second color now instead! Inside the if, put a block that can set the color variable to the number 2.

``` blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {
            agent.setSlot(color)
            agent.place(FORWARD)
            agent.move(RIGHT, 1)
            if(color == 1){
                color = 2
            }
        }
    }
```

## Step 8

What if the color was the second color? Right now, nothing changes. Let's add an else to the if and then place another ``||variables.set||`` block inside the else to set color to 1.

``` blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {
            agent.setSlot(color)
            agent.place(FORWARD)
            agent.move(RIGHT, 1)
            if(color == 1){
                color = 2
            } else {
                color = 1
            }
        }
    }
```

## Step 9

Now, our agent knows how to make a row of checker pattern, but the agent will keep trying to build in the same row instead of starting a new row! We need to teach the agent how to reset to the start of the row! AFTER the ``||loops.repeat||`` with width, but still inside of the ``||loops.repeat||`` with length, add a block that lets the agent move to the left, then find the ``||variables.width||`` variable to use as the number of blocks to move.

``` blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {
            agent.setSlot(color)
            agent.place(FORWARD)
            agent.move(RIGHT, 1)
            if(color == 1){
                color = 2
            } else {
                color = 1
            }
        }
        agent.move(LEFT, width)
    }
```

## Step 10

Now that we are at the start of the row, we need to make sure we are holding the right color again (this is because the end of the previous row might or might not be the same as the next color we need for the next row to make our checker board look correct). This time, we will not check what color we are holding, but instead what color is in front of the agent at the start of the row. Start by adding an ``||logic.if||`` from the logic section.

``` blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {
            agent.setSlot(color)
            agent.place(FORWARD)
            agent.move(RIGHT, 1)
            if(color == 1){
                color = 2
            } else {
                color = 1
            }
        }
        agent.move(LEFT, width)
        if(true){

        }
    }
```

## Step 11

Inside the condition of the if, we want to check if the inspected block in front of the agent is the same as the block that the agent is holding in it's first inventory slot. First, grab an equal sign from the logic section. Then, look for the ``||agent.inspect block||`` block for the first slot of the equals and the ``||agent.get item id||`` block for the second slot of the equals.

``` blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {
            agent.setSlot(color)
            agent.place(FORWARD)
            agent.move(RIGHT, 1)
            if(color == 1){
                color = 2
            } else {
                color = 1
            }
        }
        agent.move(LEFT, width)
        if(agent.inspect(AgentInspection.Block, FORWARD) == agent.getItemDetail(1)){

        }
    }
```

## Step 12

Inside the if, we know that the block the agent is looking at is the first block, so we want to switch to the second color. Add a block that will set the ``||variables.color||`` variable to 2. Then, add an else and set the ``||variables.color||`` to 1.

``` blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {
            agent.setSlot(color)
            agent.place(FORWARD)
            agent.move(RIGHT, 1)
            if(color == 1){
                color = 2
            } else {
                color = 1
            }
        }
        agent.move(LEFT, width)
        if(agent.inspect(AgentInspection.Block, FORWARD) == agent.getItemDetail(1)){
            color = 2
        } else {
            color =1
        }
    }
```

## Step 13

There is one more super important step, the agent is still going to try to place the blocks inside of the previous row. The agent needs to take a step back! Try adding that block!

``` blocks
let color = 0
player.onChat("checker", function (width, length) {
    agent.teleportToPlayer()
    agent.turn(LEFT_TURN)
    agent.turn(LEFT_TURN)
    agent.move(BACK, 2)
    agent.setItem(BLOCK_OF_QUARTZ, 64, 1)
    agent.setItem(POLISHED_BLACKSTONE, 64, 2)
    color = 1
    for (let index = 0; index < length; index++) {
        for (let index = 0; index < width; index++) {
            agent.setSlot(color)
            agent.place(FORWARD)
            agent.move(RIGHT, 1)
            if(color == 1){
                color = 2
            } else {
                color = 1
            }
        }
        agent.move(LEFT, width)
        if(agent.inspect(AgentInspection.Block, FORWARD) == agent.getItemDetail(1)){
            color = 2
        } else {
            color =1
        }
        agent.move(BACK, 1)
    }
```

## Step 14

Your code should now be complete! Great work! Run the code and test it! Don't forget you need to type the command name and 2 numbers, like "checker 3 5", into the chat to start the agent!

## Activity Complete!

Great job! You showed off what you know about loops, nesting, and conditions!
