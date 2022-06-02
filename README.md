# Fuel

Fuel is a toolkit for calculating fuel required to make a rocket flight.

## How to use?
Run `mix deps.get` in your shell to fetch all required dependencies and start program with `iex -S mix` command. 

Next, you have to plan your trip. The program needs two things to calculate the correct amount of fuel:
* a list of directives and targeted planets' (or moons) gravities expressed in m/s<sup>2</sup>.
* the weight of the rocket (without any fuel) expressed in kg.

Example list of directives for a mission to mars (launch from Earth, land on Mars, launch from Mars and land on Earth):

```elixir
[{:launch, 9.807}, {:land, 3.711}, {:launch, 3.711}, {:land, 9.807}]
```

Let's say that the weight of rocket is 14606 kg. Now you are able to calculate required fuel amount for planned trip.

```elixir
iex(1)> directives = [{:launch, 9.807}, {:land, 3.711}, {:launch, 3.711}, {:land, 9.807}]
[launch: 9.807, land: 3.711, launch: 3.711, land: 9.807]
iex(2)> rocket_weight = 14606
14606
iex(3)> Fuel.calculate(rocket_weight, directives)
33388
```