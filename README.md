import random

name= input("Please enter your name: ")
pc_hp = 10
me_hp = 10
itert= 0

while True:
    if pc_hp <= 0 or me_hp <= 0:
        break

    input("press enter if you are ready...")
    print("-"*50)
    print(f"Iter: {itert}")
    print("-"*50)
    damage = random.randint(1,3)

    if itert %2:
        investigate = input("defence or attack? (0: defense, 1: attack): ")
        if investigate == "0":
            print("You got zero damage! ")
        elif investigate == "1":
            chance = random.randint(0,1)
            if chance == 0:
                print("you attacked unsuccessfuly!")
                me_hp = me_hp - (damage*2)
            else:
                print("You attacked successfuly!")
                pc_hp = pc_hp -(damage*2)
    else:
        print("""
        your turn to attack.
        if pc can defense, it will not get damage.
        if pc can attack to you successfuly, you will get double damage!
        """)
        pc_choice = random.randint(0,1)
        if pc_choice == 0:
            print("pc defensed itself successfully!")
        else:
            print("pc has attacked!")
            chance = random.randint(0,1)
            if chance == 0:
                pc_hp = pc_hp -(damage*2)
            else:
                me_hp = me_hp - (damage*2)

    print(f"""
    pc's life: {pc_hp}
    {name}'s life: {me_hp}
    """)
    itert +=1

if me_hp > pc_hp:
    print(f"{name} has won!")
elif me_hp <pc_hp:
    print("PC has won the competition!")
