### @flyoutOnly 1

## Step 1

```template
player.onItemInteracted(BLAZE_ROD, function () {})
```

In this task, we need to fix some holes and repair some broken cracked 'n'
mouldy stones. Your agent has plenty of polished Andesite to fill and repair
the path with. Place your code within the ``||player: on item used||`` section,
then right click your **blaze rod** when you want to run the code.
Hit the **Next** button to continue.

## Step 2
First, we need to move your agent from the starting diamond block onto the first
row of the path so we can get onto fixing the path. Try using the
``||agent:agent move forward / right||`` commands to position your agent.

```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    agent.move(RIGHT, 1)
})
```

## Step 3
Now we need to setup some loops for each row of path we have. *remember that
rows are across the way*. We can use the ``||loops: repeat for||``. Then we also
need loop for each block we need to check on each row in that.
```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    for (let index = 0; index < 3; index++) {
        for (let index = 0; index < 9; index++) {
        }
    }
})
```

## Step 4
Now lets place the code inside the inner repeat, this will be the block of code 
that check if the path has a gap and replaces it with as block of **Andesite**.
Try using ``||logic: if true then||`` and ``||logic: 0 = 0||`` 
for working out when there's an air block. The you can use
``||agent: agent place forward / down||`` to place blocks
```blocks
for (let index = 0; index < 3; index++) {
    if (agent.inspect(AgentInspection.Block, DOWN) == AIR) {
        agent.place(DOWN)
    }
}
```

## Step 5
Continuing from the last step, Now do the same thing under the last 
``||logic: if true then||``, but when you hit a
**Mossy Cobblestone** block you replace it with a **Andesite**. 
``||agent: agent destroy forward / down||`` will help with this.
```blocks
for (let index = 0; index < 3; index++) {
    if (agent.inspect(AgentInspection.Block, DOWN) == MOSS_STONE) {
        agent.destroy(DOWN)
        agent.place(DOWN)
    }
}
```

## Step 6
Now after we've check the block the agent is sitting on we need to move
forward to the next block. *Hint Hint:* ``||agent:agent move forward||``
```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    for (let index = 0; index < 3; index++) {
        for (let index = 0; index < 9; index++) {
            agent.move(FORWARD, 1)
        }
    }
})
```

## Step 7
After the agent has gone through each block in the row for the path, we need it
to move back to where it started on the row and go onto the next row. At the end
after it goes through each row it should also end on the gold block. You can use
``||agent:agent move forward / back / right||`` to 
```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    for (let index = 0; index < 3; index++) {
        for (let index = 0; index < 9; index++) {
        }
        agent.move(BACK, 8)
        agent.move(RIGHT, 1)
    }
})
```

## Step 8
Now move your agent to the diamond block and have it face towards the path,
and try out the program you've just wrong. If you're having issues or want to
start again, hit the reset button on the wall next to you. **Good Luck**