# 🥄 spoonacular 🥄
---

[Spoonacular](http://spoonacular.com/) is a food and recipe website that offers a freemium API with over fifty different endpoints.

My Python client for the Spoonacular API is available here: [`spoonacular`](https://github.com/johnwmillr/SpoonacularAPI)

### Examples

```python
import spoonacular as sp
api = sp.API("your_api_key_here")

# Parse an ingredient
response = api.parse_ingredients("3.5 cups King Arthur flour", servings=1)
data = response.json()
print(data[0]['name'])
>>>"flour"

# Detect text for mentions of food
response = api.detect_food_in_text("I really want a cheeseburger.")
data = response.json()
print(data['annotations'][0])
>>>{"annotation": "cheeseburger", "tag":"dish"}

# Get a random food joke
response = api.get_a_random_food_joke()
data = response.json()
print(data['text'])
>>>"People are a lot less judgy when you say you ate an 'avocado salad' instead of a bowl of guacamole."
```

## Documentation
 - [Spoonacular website](https://spoonacular.com/food-api)
 - [RapidAPI](https://rapidapi.com/spoonacular/api/Recipe%20-%20Food%20-%20Nutrition)
 - [DocScraper](https://github.com/johnwmillr/DocScraper)
