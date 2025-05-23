# CS635-Problem-Set-3-solution

Download Here: [CS635 – Problem Set #3 solution](https://jarviscodinghub.com/assignment/cs635-problem-set-3-solution/)

For Custom/Original Work email jarviscodinghub@gmail.com/whatsapp +1(541)423-7793

1 Sugar Cane Production
The harvest of cane sugar in Australia is highly mechanized. The sugar cane is immediately
transported to a sugar house in wagons that run on a network of small rail tracks. The sugar
content of a wagon load depends on the field it has been harvested from and on the maturity
of the sugar cane. Once harvested, the sugar content decreases rapidly through fermentation
and the wagon load will entirely lose its value after a certain time. At this moment, eleven
wagons all loaded with the same quantity have arrived at the sugar house. They have been
examined to find out the hourly loss and the remaining life span (in hours) of every wagon;
these data are summarized below:
Lot 1 2 3 4 5 6 7 8 9 10 11
Loss(kg/h) 43 26 37 38 13 54 62 49 19 28 30
Life span (h) 8 8 2 8 4 8 8 8 8 8 8
Every lot may be processed by any of the three, fully equivalent production lines of the
sugar house. The processing of a lot takes two hours. It must be finished at the latest at the
end of the life span of the wagon load.
1.1 Problem
The manager of the sugar house wishes to determine a production schedule for the currently
available lots that minimizes the total loss of sugar. Write a GAMS model to do this. Ensure
that you display only when each wagon is unloaded and the loss of product from each wagon
in each unloading period.
2 House Captain
You have been selected to be the House captain for the Gryffindor Quidditch team. Congratulations! Your job is to select the players of the team to maximize the overall quality. You
know the quality of each player for each position, and the team quality is merely the sum of
the players’ quality for their assigned positions. For those of you without 10-year old children,
a Quidditch team consists of players of four different positions: seeker, chaser, keeper, and
beater. On a team there are 2 beaters, 3 chasers, one keeper, and one seeker.
Here is the top data for your gams file.
Problem 2 Page 1
CS635 Problem Set #3 Prof. Michael Ferris
set player /Harry_Potter, Ron_Weasley, Fred_Weasley, George_Weasley,
Oliver_Wood, Angelina_Johnson, Ginny_Weasley, Hermione_Granger,
Neville_Longbottom, Seamus_Finnegan, Dean_Thomas,
Romilda_Vane, Colin_Creevy, Dennis_Creevy, Lavender_Brown,
Alicia_Spinnet, Katie_Bell, Cormac_McLaggen,
Demelza_Robinson /
position /seeker, chaser, beater, keeper/ ;
parameter quality(player, position) ;
option seed = 42;
quality(player,’seeker’) = uniform(32,36);
quality(player,’chaser’) = uniform(38,41);
quality(player,’beater’) = uniform(30,35);
quality(player,’keeper’) = uniform(28,38);
quality(’Harry_Potter’, ’seeker’) = 42 ;
2.1 Problem
Write a linear programming model to maximize the quality of the Gryffindor house team. At
the end of the program, display the numerical quality of the team (in a parameter named
houseScore), and also display the set of students chosen to be a member of the team (in a
dynamic set named Gryffindor team). The code below can be used as a template.
parameters houseScore;
housescore = teamQuality.L ;
set Gryffindor_team(player,position) ;
Gryffindor_team(player,position) = yes$(x.L(player,position) > 0.001) ;
option Gryffindor_team:0:0:1;
display houseScore;
display Gryffindor_team ;
3 Milk production
Happy Milk Distributors (HMD) purchases raw milk from farmers in two regions: A and B.
Prices, butterfat content and separation properties of the raw milk differ between the two
regions. HMD processes the raw milk to produce cream and milk to desired specifications for
distribution to the consumers.
Region A Raw Milk Milk from region A is 54 cents per gallon up to 500 gallons and 58
cents per gallon in excess of 500 gallons. There is no upper bound on the amount that can be
purchased. Raw milk from Region A has 25% butterfat and when separated (at 5 cents per
gallon) it yields two “milks”, one with 41% butterfat and another with 12% butter fat.
The volume of milk is conserved in all separation processing.
Region B Raw Milk The purchase price for milk from region B is 38 cents per gallon up
to 700 gallons and 42 cents per gallon thereafter. Raw milk from Region B has 15% butterfat
Problem 3 Page 2
CS635 Problem Set #3 Prof. Michael Ferris
and when separated (at 7 cents per gallon) yields two “milks”, one with 43% butterfat and
another with 5% butterfat.
Production Process After the milk is purchased and collected at the plant, it is either
mixed directly or separated and then mixed. The mixing is done at no cost, and its purpose is
to produce cream and milk to specifications. For example, some of the raw milk from Region A
may be separated and then mixed, and some of it may be mixed directly (i.e., without having
been separated).
Demand and Selling Price The demand and selling price are described in the following
table:
Minimum req’d Max vol dem Selling price
% of butterfat (gallons) (cents/gallon)
Cream 40 250 150
Milk 20 2000 70
For example, all the cream produced must have at least 40% butterfat, it sells at $1.50 per
gallon, and as much as 250 gallons of the cream produced can be sold.
3.1 Problem
Assuming free disposal, formulate a linear program in GAMS which when solved enables
HMD to maximize its profit.
3.2 Problem
Suppose that the purchase price for milk from region B were 50 cents per gallon up to 700
gallons and 30 cents per gallon thereafter. Can you still formulate the profit maximization
problem as a linear program? If not, why not?
