# RECIPE-BOOK-MANAGEMENT-SYSTEM-USING-PYTHON
class Recipe:
    def __init__(self, name, ingredients, instructions):
        self.name = name
        self.ingredients = ingredients
        self.instructions = instructions

class RecipeBook:
    def __init__(self):
        self.recipes = []

    def add_recipe(self, recipe):
        self.recipes.append(recipe)
        print(f"Recipe '{recipe.name}' added successfully.")

    def remove_recipe(self, recipe_name):
        for recipe in self.recipes:
            if recipe.name.lower() == recipe_name.lower():
                self.recipes.remove(recipe)
                print(f"Recipe '{recipe_name}' removed successfully.")
                return
        print(f"Recipe '{recipe_name}' not found.")

    def search_recipe(self, keyword):
        found_recipes = []
        for recipe in self.recipes:
            if keyword.lower() in recipe.name.lower():
                found_recipes.append(recipe)
        if found_recipes:
            print(f"Found {len(found_recipes)} recipes with '{keyword}':")
            for recipe in found_recipes:
                print(recipe.name)
        else:
            print(f"No recipes found with '{keyword}'.")

    def display_all_recipes(self):
        if self.recipes:
            print("Recipes in the book:")
            for recipe in self.recipes:
                print(recipe.name)
        else:
            print("No recipes in the book.")

# Function to get user input for adding a recipe
def get_recipe_input():
    name = input("Enter recipe name: ")
    ingredients = input("Enter ingredients (comma-separated): ").split(",")
    instructions = input("Enter instructions: ")
    return Recipe(name, ingredients, instructions)

# Example usage:
book = RecipeBook()

while True:
    print("\nRecipe Book Management")
    print("1. Add Recipe")
    print("2. Remove Recipe")
    print("3. Search Recipe")
    print("4. Display All Recipes")
    print("5. Exit")
    choice = input("Enter your choice: ")

    if choice == "1":
        recipe = get_recipe_input()
        book.add_recipe(recipe)
    elif choice == "2":
        recipe_name = input("Enter the name of the recipe to remove: ")
        book.remove_recipe(recipe_name)
    elif choice == "3":
        keyword = input("Enter keyword to search for recipes: ")
        book.search_recipe(keyword)
    elif choice == "4":
        book.display_all_recipes()
    elif choice == "5":
        print("Exiting...")
        break
    else:
        print("Invalid choice. Please enter a valid option.")

