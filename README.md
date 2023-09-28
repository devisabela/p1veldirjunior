# p1veldirjunior
Questões da P1 segundo semestre de P.O.O


<?php

///////////// professor, ignopre meus comentários desde já no código. tdah é assim. att, isabela bernardi viegas de lima 

class Conta {
    private $banco;
    private $agencia;
    private $numeroConta;
    private $saldo;

    public function __construct($banco, $agencia, $numeroConta, $saldo) {
        $this->banco = $banco;
        $this->agencia = $agencia;
        $this->numeroConta = $numeroConta;
        $this->saldo = max(0, $saldo); // Garante saldo não negativo
    }

 //get e set
    public function getBanco() {
        return $this->banco;
    }

    public function setBanco($banco) {
        $this->banco = $banco;
    }

    public function getAgencia() {
        return $this->agencia;
    }

    public function setAgencia($agencia) {
        $this->agencia = $agencia;
    }

    public function getNumeroConta() {
        return $this->numeroConta;
    }

    public function setNumeroConta($numeroConta) {
        $this->numeroConta = $numeroConta;
    }

    public function getSaldo() {
        return $this->saldo;
    }

    public function setSaldo($saldo) {
        $this->saldo = max(0, $saldo);
    }

    public function deposito($valor) {
        if ($valor > 0) {
            $this->saldo += $valor;
            return true;
        } else {
            return false;
        }
    }

    public function saque($valor) {
        if ($valor > 0 && $valor <= $this->saldo) {
            $this->saldo -= $valor;
            return $valor;
        } else {
            return false;
        }
    }
}

  // classes CONTAS
$conta1 = new Conta("Banco A", "001", "211274", 650);
$conta2 = new Conta("Banco B", "002", "020101", -65);

// DEP
$conta1->deposito(150);
$conta2->deposito(-100);  // COLOCANDO VALOR NEGATIVO

// SAQ
$saque1 = $conta1->saque(700);
$saque2 = $conta2->saque(1000);  // VALOR SUPERIOR AO DO SALDO

// INF
echo "Conta 1: Banco - " . $conta1->getBanco() .
    ", Agência - " . $conta1->getAgencia() .
    ", Número da Conta - " . $conta1->getNumeroConta() .
    ", Saldo - " . $conta1->getSaldo() . "\n";

echo "Saque efetuado da Conta 1: " . ($saque1 !== false ? $saque1 : "Saque não realizado") . "\n";

echo "Conta 2: Banco - " . $conta2->getBanco() .
    ", Agência - " . $conta2->getAgencia() .
    ", Número da Conta - " . $conta2->getNumeroConta() .
    ", Saldo - " . $conta2->getSaldo() . "\n";

echo "Saque efetuado da Conta 2: " . ($saque2 !== false ? $saque2 : "Saque não realizado") . "\n";
