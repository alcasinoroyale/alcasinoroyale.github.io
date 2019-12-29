---
layout: post
title:      "Creating Sorted Tables in Angular"
date:       2019-12-29 16:53:06 -0500
permalink:  creating_sorted_tables_in_angular
---

One of the main components of the front-end development project that I've been working on is a sortable table in Angular. For this post, I'm going to focus on how I would convert the game objects from my Ruby on Rails application into a sortable table for Angular. A great feature of Angular is that you can create classes and models with individual typescript files that you can import into your components. To get started, you can build game.ts, which will describe the Game class as well as the array of objects inside of it. There are several attributes attached to the original game object, but for this example, I only want to display six of them inside the table. A Game will have a name, objective, # of players, reward points, genre, and a category. 

**game.ts**
*Game Class*

```
export class Game {
  name: string;
  objective: string;
  players: number;
  rewardPoints: number;
  genre: string;
  category: string;
}
```

After creating the game class, we can also start building an array of objects. This can be accomplished by creating a variable with the const keyword. This variable will act on the Game class so that we have access to the array of objects and display the game details inside the table.

**game.ts**
*Array of Game Objects*

```
export const GAMES: Game[] = [
  {
	 name: 'Air Hockey',
	 objective: 'First player to score 7 goals wins the game'
	 players: 2,
	 rewardPoints: 80,
	 genre: 'Sport',
	 category: 'Table Game'
	},
	{
	 name: 'The Witcher 3: Wild Hunt',
	 objective: 'Explore the world and complete the character's journey through missions and side quests'
	 players: 1,
	 rewardPoints: 130,
	 genre: 'Role Playing',
	 category: 'Video Game'
	},
	{
	 name: 'Scrabble',
	 objective: 'Player with the highest score wins the game'
	 players: 2,
	 rewardPoints: 80,
	 genre: 'Word Game',
	 category: 'Board Game'
	},
	{
	 name: 'Pinball',
	 objective: 'Climb the overall leaderboard'
	 players: 1,
	 rewardPoints: 100,
	 genre: 'Arcade',
	 category: 'Table Game'
	}
]
```

Since I want to display the table information inside of a specific component, I would first create a component with `ng generate component games-table`. This creates an HTML, CSS, and TS file for the games-table component.

Inside games-table.ts, you want to begin with a simple sketch before you start creating functions, but make sure to import the game class as well as the array of objects that holds the attributes for each specific game.

**games-table.component.ts**
*Initial Typescript for Games Table Component*

```
import { Component } from @ angular/core'
import { Game, GAMES} from '../game'

@Component({
  selector: 'app-games-table'
  templateUrl: './games-table.component.html'
  styleUrls: [./games-table.component.css']
	})
	
	export class GamesTableComponent {
	
	constructor(){}
	
}
```

After building the game class and component, you want to start constructing the table inside of the HTML file. For a sorted table, there are many strategies that you can utilize, but one way that will save development time while keeping your table organized is the MatSortModule. This is downloaded through the @angular/material package. 

To confirm that the module was installed successfully, check the dependencies inside of package.json so that it lists `"@angular/material"` with the latest version. Also, import the module into app.module.ts with `import { MatSortModule } from '@angular/material/sort'` and then add it as an import inside of @NgModule. It will likely not render the page or display the appropriate error in the console if the module isn't loaded correctly.

**games-table.component.html**
*Sorted Games Table*

```
<h2>Games</h2>

<div class="gamesTable">
<table class="table table striped" matSort (matSortChange)="sortGames($event)
<thead>
 <tr>
	<th mat-sort-header="name" scope="col">Name</th>
	<th mat-sort-header="objective" scope="col">Objective</th>
	<th mat-sort-header="players" scope="col"># of Players</th>
	<th mat-sort-header="rewardPoints" scope="col">Reward Points</th>
	<th mat-sort-header="genre" scope="col">Genre</th>
	<th mat-sort-header="category" scope="col">Category</th>
 </tr>
</thead>
<tbody>
 <tr *ngFor="let game of sortedGames">
  <td>game.name</td>
  <td>game.objective</td>
  <td>game.players</td>
  <td>game.rewardPoints</td>
  <td>game.genre</td>
  <td>game.category</td>
 </tr>
</tbody>
</table>
</div>
```

The headings and the attributes for each game will be displayed inside the table, but we still need to build the appropriate functions to sort the table. Each attribute inside the sorted list should also be closed with {}.

Arguably the most crucial code inside the table is `matSort (matSortChange)="sortGames($event)`
This is referring to the sortGames function that will be constructed near the the end of this post, but first you want to make sure that the file looks like this:

**games-table.component.ts**
*Before sortGames function*

```
import { Component } from @ angular/core'
import { Game, GAMES} from '../game'
import { Sort } from '@angular/material/sort';

@Component({
  selector: 'app-games-table'
  templateUrl: './games-table.component.html'
  styleUrls: [./games-table.component.css']
	})
	
	export class GamesTableComponent {
	
	games = GAMES;
	sortedGames: Game[];
	
	constructor(){
	  this.sortedGames = this.games.slice()
	}
}
```

A few lines of code to note here is that Sort is imported from the angular material package, the Game array is now set to sortedGames, and we also implement the slice method inside of the constructor so the correct slice of data is passed into the table when the headings are sorted by the user. The sortGames function should then look like this below:

**games-table.component.ts** 
*Sorting Functions*

```
sortGames(sort: Sort) {
 const data = this.games.slice()
 if (!sort.active || sort.direction === '') {
  this.sortedGames = data;
	return;
	}
	
this.sortedGames = data.sort((a, b) => {
const isASC = sort.direction === 'asc';
switch (sort.active) {
   case 'name': return compare(a.name, b.name, isAsc);
   case 'objective': return compare(a.objective, b.objective, isAsc);
   case 'players': return compare(a.players, b.players, isAsc);
   case 'rewardPoints': return compare(a.rewardPoints, b.rewardPoints, isAsc);
   case 'genre': return compare(a.genre, b.genre, isAsc);
   case 'category': return compare(a.category, b.category, isAsc);
	 default: return 0;
   }
  })
 }
}

function compare(a: number | string, b: number | string, isAsc: boolean) {
  return (a < b ? -1 : 1) * (isAsc ? 1 : -1);
}
```

The sortGames method first takes an argument of sort and then sets the specific slice of each to the data. If sort isn't active or the sort direction is empty, it will display the table with its original components. Each time a heading is clicked, the data inside the table will be sorted in ascending order based on the content for the specific game object. In this example, the content is a string or a number. If the names of each game are being sorted, the first row of the table would be all of Air Hockey's information. If the Names heading is clicked again, the sort direction would then switch the names to descending order.




