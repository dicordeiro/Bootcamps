let enumHeroType = {
  guerreiro: 0,
  0: "guerreiro",
  mago: 1,
  1: "mago",
  monge: 2,
  2: "monge",
  ninja: 3,
  3: "ninja",
};
let enumToAttack = {
  0: "espada",
  1: "magia",
  2: "artes marciais",
  3: "shuriken",
};

function randomRange(from, to) {
  return Math.floor(Math.random() * (to - from + 1)) + from;
}

class gameCharacter {
  constructor(
    name,
    age,
    hp,
    strength,
    heroType = enumHeroType[randomRange(0, 3)]
  ) {
    this.name = name;
    this.age = age;
    this.hp = hp;
    this.strength = strength;
    this.indexHeroType =
      typeof heroType === "number" ? heroType : enumHeroType[heroType] | 0;
  }
  toAttack(enemy, strength) {
    strength = strength + this.strength / 2;
    console.log(
      `   o ${enumHeroType[this.indexHeroType]} atacou usando ${
        enumToAttack[this.indexHeroType]
      }`
    );
    let damage = Math.floor(randomRange(1 + strength / 3, 20 * strength));
    console.log(`   e causou ${damage} de dano\n`);

    enemy.takesDamage(damage);
  }
  takesDamage(damage) {
    console.log(`      ${this.name} sofreu ${damage} de dano`);
    this.hp = this.hp - damage;
    if (this.hp <= 0) {
      console.log(`       ${this.name} foi morto\n`);
    } else {
      console.log(`       ${this.name} ficou com ${this.hp} de hp `);
    }
  }
  targetEnemy(targets, combatSituation) {
    if (this.hp <= 0) {
      return console.log(`     ${this.name} esta morto...\n`);
    }
    let target = targets[randomRange(0, targets.length - 1)];
    if (target.hp <= 0) {
      console.log(
        `     ${this.name} olhando inimigo ${target.name} morto...\n`
      );
      return;
    } else {
      this.toAttack(target, combatSituation);
    }
  }
}

const players = [gameCharacter.prototype];
players[0] = new gameCharacter("Junior", 100, 10, 7, enumHeroType.mago);
players[1] = new gameCharacter("DIO", 220, 22, 22);

const enemies = [gameCharacter.prototype];
enemies[0] = new gameCharacter("Luis", 100, 10, 7, enumHeroType[randomRange]);
enemies[1] = new gameCharacter("Ze", 57, 22, 22);

let allDead;
let victory;
while (!allDead) {
  allDead = true;

  for (let player of players) {
    console.log(`player ${player.name} turn\n`);
    if ((player.indexHeroType = enumHeroType.mago)) {
      player.targetEnemy(enemies, player.strength + randomRange(2, 6));
    } else if ((player.indexHeroType = enumHeroType.guerreiro)) {
      player.targetEnemy(enemies, player.strength + randomRange(0, 2));
    } else {
      player.targetEnemy(enemies, player.strength / 3);
      player.targetEnemy(enemies, player.strength / 3);
      player.targetEnemy(enemies, player.strength / 3);
    }
    allDead &&= player.hp <= 0;
    victory = false;
  }
  if (!allDead) {
    allDead = true;
    for (let enemy of enemies) {
      console.log(`enemy ${enemy.name} turn\n`);
      if ((enemy.indexHeroType = enumHeroType.mago)) {
        enemy.targetEnemy(players, enemy.strength + randomRange(0, 3));
      } else if ((enemy.indexHeroType = enumHeroType.guerreiro)) {
        enemy.targetEnemy(players, enemy.strength + randomRange(0, 1));
      } else {
        enemy.targetEnemy(players, enemy.strength / 2);
        enemy.targetEnemy(players, enemy.strength / 2);
      }
      allDead &&= enemy.hp <= 0;
      victory = true;
    }
  }
}

if (victory) {
  console.log(`VITORIA\n`);
} else {
  console.log(`DERROTA\n`);
}
