# Data Analyst recruitment test

- [Data Analyst recruitment test](#data-analyst-recruitment-test)
- [Introduction](#introduction)
- [Objective](#objective)
- [Sources](#sources)
  - [Booking](#booking)
  - [Battlepass](#battlepass)
  - [Game](#game)
- [Data](#data)
  - [Bookings](#bookings)
  - [Locations](#locations)
  - [Terrains](#terrains)
  - [Battlepass](#battlepass-1)
  - [Game history](#game-history)
  - [Game history players](#game-history-players)
  - [Experiences](#experiences)
- [Bonus questions](#bonus-questions)

# Introduction

First, thank you for taking the time to do our technical test. We **strongly** recommend you to read entirely this test before to start.

The goal of this test is to answer questions about data. We have multiple sources of data: `Booking`, `Battlepass` and `Game`. Every source have his own set of questions and data.

# Objective

In order to complete the test you must answer to the questions of the different sources.

You must answer at least to **two** questions per source.

An answer of a question is complete when:

- A representation for the question is given. You are free to give any type of representation: `table`, `chart`, etc.
- You commented your answer:
  - What is the interesting thing the data is showing us?
  - Optional: What missing data would be interesting to track here?
  - Optional: What analysis would you suggest? Does it seem relevant to you? If not, what would you suggest?

**Bonus:** You can add up to 2 questions you find interesting to analyze.

# Sources

## Booking

- Evolution of the number of participant.
- Distribution of the peak/off-peak hours.
- Distribution of the number of participants per time slot (15-16h, 16-17h, etc.).
- Fill rate of the time slot.

## Battlepass

- Distribution of the active Battlepass plans.
- Evolution of the active Battlepass per month.
- Rate of return for a battle pass after disengagement.

## Game

- Distribution of the different game mode played.
- Tendency of players to play together.
- Calculate an indicator showing the performance of players.

# Data

## Bookings

A booking is a reservation made by a user in order to play one session of EVA.

Data from the `2023-08-01` to the `2023-10-01` excluded.

| column              | description                                                                                 |
| ------------------- | ------------------------------------------------------------------------------------------- |
| location_id         | `ID` of the location                                                                        |
| terrain_id          | `ID` of the terrain used for the booking                                                    |
| user_id             | `ID` of the user who made the booking                                                       |
| participant_number  | `Number` of participant the booking is for                                                  |
| is_battlepass       | `Boolean` showing if the booking was made using a Battlepass (**for only one participant**) |
| status              | `Enum` status of the booking: `confirmed` or `cancelled`                                    |
| session_date        | `Date` of the booking                                                                       |
| created_at          | `Timestamp` of when the when it has been created                                            |
| session_starts_at   | `Timestamp` of when the booking session starts                                              |
| session_ends_at     | `Timestamp` of when the booking session ends                                                |
| is_peak_hour        | `Boolean` showing if the booking is during the peak hours or not                            |
| is_competitive_mode | `Boolean` showing if the booking is in competitive mode (session limited to 8 participant)  |

## Locations

A location is a physical place where EVA terrains are availables.

| column | description                 |
| ------ | --------------------------- |
| id     | `ID` of the location        |
| name   | `Text` name of the location |

## Terrains

A terrain is an EVA arena where an EVA game can be played.

| column      | description                 |
| ----------- | --------------------------- |
| id          | `ID` of the terrain         |
| location_id | `ID` of the location        |
| name        | `text` name of the terrain  |
| max_player  | `Number` max of participant |

## Battlepass

A Battlepass is a subscription allowing the user to play a limited number of game session. This is a monthly subscription with 3 different plans.

Data from the `2023-08-01` to the `2023-10-01` excluded.

| column               | description                                                                                                                                          |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                   | `ID` of the Battlepass                                                                                                                               |
| user_id              | `ID` of the user who subscribed to the Battlepass                                                                                                    |
| should_cancel        | `Boolean` showing if the user wants to cancel or not his Battlepass at the end of the current month                                                  |
| status               | `Enum` status: `activated`, `cancelled`, `fail1`/`fail2` (renewal failed once or twice)                                                              |
| created_at           | `Timestamp` of when the when it has been created. **Represents the date when the subscription has started.**                                         |
| expiration_timestamp | `Timestamp` of when ends the current month. **Represents the date when the renewal will occurs if the user did not ask to cancel his subscription.** |
| subscription_plan    | `Enum` plan: `ESSENTIAL`, `PLUS`, `ULTRA`                                                                                                            |
| renewal_count        | `Number` of renewal made                                                                                                                             |

## Game history

A Game history is a game report created at the end of a EVA game. It contains general information about the game.

Data from the `2023-09-01` to the `2023-09-15` excluded.

| column     | description                                                                    |
| ---------- | ------------------------------------------------------------------------------ |
| id         | `ID` of the game history                                                       |
| duration   | `Number` of seconds.                                                           |
| map        | `Number` game map identifier                                                   |
| team1Score | `Number` of points of the team one. **For player versus player modes.**        |
| team2Score | `Number` of points of the team two. **For player versus player modes.**        |
| terrainId  | `ID` of the terrain where the game was played                                  |
| created_at | `Timestamp` of when the when it has been created                               |
| score      | `Number` of points made for the game. **For player versus environment modes.** |
| mode       | `Enum` mode of the game.                                                       |

## Game history players

A Game history player is a user specific game report created at the end of a EVA game. It contains user's information about the game.

Data from the `2023-09-01` to the `2023-09-15` excluded.

| column           | description                                |
| ---------------- | ------------------------------------------ |
| assists          | `Number` of assists                        |
| deaths           | `Number` of deaths                         |
| kills            | `Number` of kills                          |
| inflictedDamage  | `Number` of damage inflicted               |
| maxSpeed         | `Number` representing the max speed        |
| rank             | `Number` rank in the game                  |
| score            | `Number` of points for the game            |
| team             | `Text` name of the team the player were in |
| traveledDistance | `Number` in meter traveled by the player   |
| gameHistoryId    | `ID` of the game history                   |
| userId           | `ID` of the user                           |

## Experiences

An experience give the current level of a user in the game.

| column | description                |
| ------ | -------------------------- |
| userId | `ID` of the user           |
| level  | `Number` level of the user |

# Bonus questions

Please answer the following questions in a markdown file called `bonus_questions.md`.

1. How are you feeling about our [game and locations](https://www.eva.gg)?
2. Are you a gamer? Which games do you play?
