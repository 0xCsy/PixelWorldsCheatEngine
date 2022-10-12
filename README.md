<h3 align="center">Pixel Worlds - Cheat Engine</h3>

<details>
  <summary>Summary</summary>
  <ol>
    <li>
      <a href="#introduction">Introduction</a>
    </li>
    <li>
      <a href="#prerequisites">Prerequisites</a>
    </li>
    <li>
      <a href="#tutorial">Tutorial</a>
      <ul>
        <li><a href="#implementation">implementation</a></li>
        <li><a href="#basic">basic</a></li>
      </ul>
    </li>
  </ol>
</details>

## Introduction

A short tutorial to understand how to integrate cheat engine on pixel worlds.

Why should you make your own cheat table? Nowaday everything related to pixel worlds has a steler, so you may get virus or your account will be stolen.

You will understanding what to change, it's a basic understanding of how to use cheat engine on unity game, you will learn how to change integer, how to skip a function call,...

## Prerequisites

Download the lastest version of cheat engine: https://www.cheatengine.org

## Tutorial

### implementation
1. Open the game file
2. Open cheat engine or the source from this repo
3. File -> Open Process -> Pixel Worlds (now the cheat engine should be attach to the game, you can now overwrite the game memory)
4. Mono -> Activate Mono Features (with mono feature you will be able to save sometime if the game has update, learn more <a href="https://wiki.cheatengine.org/index.php?title=Mono">Cheat Engine Wiki - Mono</a> and <a href="https://www.mono-project.com/docs/">Mono - Documentation </a>)
5. You can now use the source code.

### basic
1. Mono -> Mono Dissector (with mono dissector, you will be able to review the mono class, most of the time the game script is located on the Assembly-CSharp.dll but some developper may use differente one.)

![image](https://user-images.githubusercontent.com/91699796/195326496-2efdba52-276f-4d30-b70e-92200c20563d.png)

2. For this first tutorial we will be try to unlock all recipes (for steam version), inside the Mono Dissector -> Assembly-CSharp.dll -> look for the class PlayerData -> Methods -> HasUnlockedRecipe.

![image](https://user-images.githubusercontent.com/91699796/195327060-783706e0-5e2d-44cf-8cf1-1f1cc5d42ed1.png)

3. After founding the method you can see 'HasUnlockedRecipe(blockType: World.BlockType):System.Boolean', Boolean always return True or False, on binary 0 represent False, and 1 represent True.
4. Go to your cheat engine and open Memory View, right click on any address -> Go To Address (we know the class and the method so it will be easy to found the address) -> Enter: PlayerData.HasUnlockedRecipe (Format: Class.Method).

![image](https://user-images.githubusercontent.com/91699796/195327428-7c2bf15e-9886-41b1-a330-d1fe4e3be443.png)

5. On the memory viewer, you can see 3 columns (Address, Bytes, Opcode),we will make change through Opcode, for the Opcode of HasUnlockedRecipes you can see for the first line mov [rsp+08],rbx and the second line push rdi,... So what should we do to unlock all recipe?

![image](https://user-images.githubusercontent.com/91699796/195327548-390367db-cca6-4db0-8944-9a9c475f71d5.png)

6. Left click on the Opcode first line and change it to mov eax,1 and the second line to ret, easy right? so for a simple understanding with mov eax,1 you change the result to 1 and ret you ended the function.

![image](https://user-images.githubusercontent.com/91699796/195327659-da482c60-b460-4528-805a-75aa618bdeb0.png)

7. Result

![image](https://user-images.githubusercontent.com/91699796/195328072-4a429685-e03b-4ccd-84fe-da34b140844d.png)

