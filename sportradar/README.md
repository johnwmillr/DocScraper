# Sportradar APIs
---

[Sportradar](http://sportradar.com/) is a company that provides extensive APIs for a number of professional sports including soccer, basketball, and multiple eSports leagues.

My Python client for the Sportradar APIs is available here: [`sportradar`](https://github.com/johnwmillr/SportradarAPIs)

## Examples

```python
from sportradar import Soccer

# Create an instance of the Sportradar Soccer API class
sr = Soccer.Soccer("paste your api key here")

# Get a list of all tournaments
tournaments = sr.get_tournaments().json()

# Get info on the 2018 World Cup (Teams, Rounds, etc.)
worldcup = sr.get_tournament_info(tournaments['tournaments'][4]['id']).json()

# Get more information on each team in the World Cup
teams = []
team_counter = 0
for group in worldcup['groups']:
    for team in group['teams']:
        team_counter += 1
        team_id = team['id']
        team_name = team['name']
        print("({}): {}, {}".format(team_counter, team_name, team_id))
        try:
            teams.append(sr.get_team_profile(team_id).json())
        except Exception as e:
            print("Error: {}".format(e))
        time.sleep(5) # wait 5 seconds before next API call

# Save the team data to a .json file
print("Saving the data...", end="", flush=True)
with open("world_cup_team_data.json", "w") as outfile:
    json.dump(teams, outfile)
print(" Done.")

```

## Example projects
  - [2018 FIFA World Cup player stats](https://www.johnwmillr.com/fifa-world-cup-data/)
