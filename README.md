class CoffeeMachine:
    def __init__(self):
        self.water = 400
        self.milk = 540
        self.beans = 120
        self.cups = 9
        self.money = 550

    def machine_status(self):
        print('The coffee machine has:', f'{self.water} of water', f'{self.milk} of milk',
              f'{self.beans} of coffee beans', f'{self.cups} of disposable cups',
              f'{self.money} of money', f'', sep='\n')
        self.process_method()

    def espresso(self):
        self.water -= 250
        self.beans -= 16
        self.cups -= 1
        self.money += 4

    def latte(self):
        self.water -= 350
        self.milk -= 75
        self.beans -= 20
        self.cups -= 1
        self.money += 7

    def cappuccino(self):
        self.water -= 200
        self.milk -= 100
        self.beans -= 12
        self.cups -= 1
        self.money += 6

    def check_inventory(self, coffee_type):
        if coffee_type == '1':
            if self.water < 250:
                print('Sorry, not enough water!\n')
                self.process_method()
            if self.beans < 16:
                print('Sorry, not enough beans!\n')
                self.process_method()
            if self.cups < 1:
                print('Sorry, not enough cups!\n')
                self.process_method()
            else:
                print('I have enough resources, making you a coffee!\n')
                self.espresso()
        elif coffee_type == '2':
            if self.water < 250:
                print('Sorry, not enough water!\n')
                self.process_method()
            if self.milk < 75:
                print('Sorry, not enough milk!\n')
                self.process_method()
            if self.beans < 20:
                print('Sorry, not enough beans!\n')
                self.process_method()
            if self.cups < 1:
                print('Sorry, not enough cups!\n')
                self.process_method()
            else:
                print('I have enough resources, making you a coffee!\n')
                self.latte()
        elif coffee_type == '3':
            if self.water < 200:
                print('Sorry, not enough water!\n')
                self.process_method()
            if self.milk < 100:
                print('Sorry, not enough milk!\n')
                self.process_method()
            if self.beans < 12:
                print('Sorry, not enough beans!\n')
                self.process_method()
            if self.cups < 1:
                print('Sorry, not enough cups!\n')
                self.process_method()
            else:
                print('I have enough resources, making you a coffee!\n')
                self.cappuccino()
        self.process_method()

    def coffee_choice(self):
        coffee_type = input('What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu:\n')
        if coffee_type == '1':
            self.check_inventory('1')
        elif coffee_type == '2':
            self.check_inventory('2')
        elif coffee_type == '3':
            self.check_inventory('3')
        else:
            pass
        self.process_method()

    def fill(self):
        self.water += int(input('Write how many ml of water do you want to add:\n'))
        self.milk += int(input('Write how many ml of milk do you want to add:\n'))
        self.beans += int(input('Write how many grams of coffee beans do you want to add:\n'))
        self.cups += int(input('Write how many disposable cups of coffee do you want to add:\n'))
        self.process_method()

    def take(self):
        print(f'I gave you ${self.money}\n')
        self.money = 0
        self.process_method()

    def process_method(self):
        action = input('Write action (buy, fill, take, remaining, exit):\n')
        if action == 'buy':
            print()
            self.coffee_choice()
        elif action == 'fill':
            print()
            self.fill()
        elif action == 'take':
            print()
            self.take()
        elif action == 'remaining':
            print()
            self.machine_status()
        else:
            exit()


if __name__ == '__main__':
    coffee_machine = CoffeeMachine()
    coffee_machine.process_method()
