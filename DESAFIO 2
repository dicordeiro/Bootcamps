function calcularSaldoRankeadas(vitorias, derrotas) {
    return vitorias - derrotas;
}

// Exemplo de uso da função
let vitorias = 30;
let derrotas = 20;
let saldoVitorias = calcularSaldoRankeadas(vitorias, derrotas);

let nivel;

if (vitorias < 10){
    nivel = "Ferro";
} else if (vitorias >= 10 && vitorias <= 20){
    nivel = "Bronze";
} else if (vitorias >= 21 && vitorias <= 50){
    nivel = "Prata";
} else if (vitorias >= 51 && vitorias <= 80){
    nivel = "Ouro";
} else if (vitorias >= 81 && vitorias <= 90){
    nivel = "Diamante";
} else if (vitorias >= 91 && vitorias <= 100){
    nivel = "Lendário";
} else {
    nivel = "Imortal";
}

console.log("O herói tem o saldo de " + saldoVitorias + ". Está no nível de " + nivel);
