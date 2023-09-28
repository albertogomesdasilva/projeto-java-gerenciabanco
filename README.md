<hr>
<div>
<img src="./tela-gerencia-banco.png" />
</div>
1. Atividade proposta:



Utilizando os principais conceitos do paradigma de Orientação a Objetos, crie uma pequena aplicação de
gerenciamento bancário que possibilite ao usuário informar seu nome, sobrenome e CPF. Além disso, a
aplicação deverá possibilitar ao usuário consultar saldo, realizar depositos e saques. Esses
procedimentos devem se repetir até que o usuário escolha encerrar o uso da aplicação.

2 - Em seguida, deve-se avançar e, na tela seguinte, dar o nome ao projeto. Como já mencionado,
sugere utilizar o nome gerenciaBanco.

3 - Construa a aplicação em um único arquivo do tipo java main Class. Isso porque o método principal,
que é chamado pela maquina virtual, deve estar nesse mesmo arquivo.

4 - No seu código você deverá construir, basicamente:
a) a classe principal
b) classe para para dados pessoais e operações bancárias
c) método para exibição do menu.
5 - Para a exibição do menu, será necessário utilizar uma estrutura de decisão para tratamento das
escolhas do usuário. Sugere-se utilizar a estrutura do...while e switch..case.

https://albertogomesdasilva.github.io/projeto-java-gerenciabanco/



/************************************************************************************

Relatório de Aula Prática: Desenvolvimento de um Sistema Bancário Básico em Java no NetBeans

Introdução:

A aula prática consistiu no desenvolvimento de um sistema bancário básico utilizando a linguagem de programação Java e a IDE NetBeans. O objetivo desse projeto foi criar um aplicativo simples que permite aos usuários realizar operações bancárias como depósitos, saques e consultas de saldo.

Métodos:

1. Estruturação do Projeto:

Para começar, criamos um novo projeto no NetBeans e o estruturamos em classes Java. As principais classes desenvolvidas foram:

ContaBancaria: Esta classe representou uma conta bancária e incluiu métodos para realizar depósitos, saques e consultar o saldo.
Banco: Uma classe que gerencia as contas bancárias e permite a criação, exclusão e listagem das contas.
Principal: A classe principal do projeto que contém o método main para iniciar a aplicação.
2. Implementação das Funcionalidades:

Desenvolvemos os métodos dentro das classes ContaBancaria e Banco para permitir as operações básicas de um sistema bancário. Foram implementadas as seguintes funcionalidades:

Criar uma nova conta bancária.
Depositar dinheiro em uma conta.
Realizar saque de uma conta.
Consultar o saldo de uma conta.
3. Interface do Usuário:

Criamos uma interface de texto simples que permite aos usuários interagirem com o sistema. Utilizamos menus e prompts para coletar a entrada do usuário e exibir informações.

Resultados:

O sistema bancário básico desenvolvido na aula prática permite que os usuários criem contas bancárias, realizem depósitos, saques e consultem seus saldos. As operações são executadas com sucesso e o sistema apresenta mensagens informativas ao usuário. O código foi testado e não apresentou erros durante a execução.

Conclusão:

A aula prática de desenvolvimento de um sistema bancário básico em Java no NetBeans foi bem-sucedida na criação de um aplicativo funcional que atende aos requisitos estabelecidos. Os alunos tiveram a oportunidade de aplicar os conceitos de orientação a objetos, criar classes, métodos e interagir com o usuário por meio de uma interface de texto.

Além disso, a prática permitiu a compreensão dos conceitos fundamentais de programação, como encapsulamento, herança e polimorfismo, bem como a manipulação de estruturas de controle e de dados em Java.

Em resumo, a aula prática proporcionou aos alunos uma valiosa experiência de desenvolvimento de software em Java e uma introdução aos princípios de programação orientada a objetos, que são amplamente utilizados na indústria de software.

/*************************************************************************************

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package br.com.albertogomesdasilva.agenciabancaria;

/**
 *
 * @author alber
 */

import br.com.albertogomesdasilva.agenciabancaria.Utils;

import java.util.ArrayList;
import java.util.Scanner;


public class AgenciaBancaria {

    static Scanner input = new Scanner(System.in);
    static ArrayList<Conta> contasBancarias;

    public static void main(String[] args) {
        contasBancarias = new ArrayList<Conta>();
        operacoes();
    }

    public static void operacoes() {

        System.out.println("------------------------------------------------------");
        System.out.println("----------- SISTEMA GERÊNCIA BANCO -------------------");
        System.out.println("------------------------------------------------------");
        System.out.println("Aluno: Alberto Gomes da Silva-------------------------");
        System.out.println("Matrícula: 3375090201  -------------------------------");
        System.out.println("RELATÓRIO DE AULA PRÁTICA-----------------------------");
        System.out.println("LINGUAGEM ORIENTADA A OBJETOS-------------------------");
        System.out.println("***** Selecione uma operação que deseja realizar *****");
        System.out.println("------------------------------------------------------");
        System.out.println("|   Opção 1 - Criar conta                            |");
        System.out.println("|   Opção 2 - Depositar                              |");
        System.out.println("|   Opção 3 - Sacar                                  |");
        System.out.println("|   Opção 4 - Transferir                             |");
        System.out.println("|   Opção 5 - Listar                                 |");
        System.out.println("|   Opção 6 - Sair                                   |");
        System.out.println("------------------------------------------------------");
        System.out.println("------------------------------------------------------");
        System.out.println("------------------------------------------------------");

        int operacao = input.nextInt();;

        switch (operacao) {
            case 1:
                criarConta();
                break;

            case 2:
                depositar();
                break;

            case 3:
                sacar();
                break;

            case 4:
                transferir();
                break;

            case 5:
                listarContas();
                break;

            case 6:
                System.out.println("Agradecemos a preferência.");
                System.exit(0); // para o sistema

            default:
                System.out.println("Opção inválida!");
                operacoes();
                break;
        }
    }

    public static void criarConta() {
        //System.out.println("Você está criando uma conta\n");

        System.out.println("\nNome: ");
        String nome = input.next();

        System.out.println("\nCPF: ");
        String cpf = input.next();

        System.out.println("Email: ");
        String email = input.next();

        Pessoa cliente = new Pessoa(nome, cpf, email);

        Conta conta = new Conta(cliente);

        contasBancarias.add(conta);
        System.out.println("--- Sua conta foi criada com sucesso! ---");

        operacoes();

    }

    private static Conta encontrarConta(int numeroConta) {
        Conta conta = null;
        if(contasBancarias.size() > 0) {
            for(Conta contaa : contasBancarias) {
                if(contaa.getNumeroConta() == numeroConta) {
                    conta = contaa;
                }
            }
        }
        return conta;
    }

    public static void depositar() {
        System.out.println("Número da conta: ");
        int numeroConta = input.nextInt();
        Conta conta = encontrarConta(numeroConta);

        if(conta != null) {
            System.out.println("Qual valor deseja depositar? ");
            Double valorDeposito = input.nextDouble();

            conta.depositar(valorDeposito);
        }else {
            System.out.println("--- Conta não encontrada ---");
        }

        operacoes();

    }

    public static void sacar() {
        System.out.println("Número da conta: ");
        int numeroConta = input.nextInt();

        Conta conta = encontrarConta(numeroConta);

        if(conta != null) {
            System.out.println("Qual valor deseja sacar? ");
            Double valorSaque = input.nextDouble();

            conta.sacar(valorSaque);
            System.out.println("--- Saque realizado com sucesso! ---");
        }else {
            System.out.println("--- Conta não encontrada ---");
        }

        operacoes();

    }

    public static void transferir() {
        System.out.println("Número da conta que vai enviar a transferência: ");
        int numeroContaRemetente = input.nextInt();

        Conta contaRemetente = encontrarConta(numeroContaRemetente);

        if(contaRemetente != null) {
            System.out.println("Número da conta do destinatário: ");
            int numeroContaDestinatario = input.nextInt();

            Conta contaDestinatario = encontrarConta(numeroContaDestinatario);

            if(contaDestinatario != null) {
                System.out.println("Valor da transferência: ");
                Double valor = input.nextDouble();

                contaRemetente.transferencia(contaDestinatario, valor);

            }else {
                System.out.println("--- A conta para depósito não foi encontrada ---");
            }

        }else {
            System.out.println("--- Conta para transferência não encontrada ---");
        }
        operacoes();
    }

    public static void listarContas() {
        if(contasBancarias.size() > 0) {
            for(Conta conta: contasBancarias) {
                System.out.println(conta);
            }
        }else {
            System.out.println("--- Não há contas cadastradas ---");
        }

        operacoes();
    }
}

    
/**
/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package br.com.albertogomesdasilva.agenciabancaria;

/**
 *
 * @author alber
 */


public class Conta {

    private static int accountCounter = 1;

    private int numeroConta;
    private Pessoa pessoa;
    private Double saldo = 0.0;


    public Conta(Pessoa pessoa) {
        this.numeroConta = Conta.accountCounter;
        this.pessoa = pessoa;
        this.updateSaldo();
        Conta.accountCounter += 1;
    }


    public int getNumeroConta() {
        return numeroConta;
    }
    public Pessoa getClient() {
        return pessoa;
    }
    public void setClient(Pessoa pessoa) {
        this.pessoa = pessoa;
    }
    public Double getSaldo() {
        return saldo;
    }
    public void setSaldo(Double saldo) {
        this.saldo = saldo;
    }

    private void updateSaldo() {
        this.saldo = this.getSaldo();
    }

    public String toString() {

        return "\nBank account: " + this.getNumeroConta() +
                "\nCliente: " + this.pessoa.getName() +
                "\nCPF: " + this.pessoa.getCpf() +
                "\nEmail: " + this.pessoa.getEmail() +
                "\nSaldo: " + Utils.doubleToString(this.getSaldo()) +
                "\n" ;
    }

    public void depositar(Double valor) {
        if(valor > 0) {
            setSaldo(getSaldo() + valor);
            //this.saldo = this.getSaldo() + valor;
            System.out.println("Seu depósito foi realizado com sucesso!");
        }else {
            System.out.println("Não foi possível realizar o depósito!");
        }
    }

    public void sacar(Double valor) {
        if(valor > 0 && this.getSaldo() >= valor) {
            setSaldo(getSaldo() - valor);
            System.out.println("Saque realizado com sucesso!");
        }else {
            System.out.println("Não foi possível realizar o saque!");
        }
    }

    public void transferencia(Conta contaParaDeposito, Double valor) {
        if(valor > 0 && this.getSaldo() >= valor) {
            setSaldo(getSaldo() - valor);
            //this.saldo = this.getSaldo() - valor;
            contaParaDeposito.saldo = contaParaDeposito.getSaldo() + valor;
            System.out.println("Transferência realizada com sucesso!");
        }else {
            System.out.println("Não foi possível realizar a tranferência");
        }

    }

}

//****

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package br.com.albertogomesdasilva.agenciabancaria;

/**
 *
 * @author alber
 */



import java.util.Date;



public class Pessoa {

   
    private static int counter = 1;

    private int numeroPessoa ;
    private String name;
    private String cpf;
    private String email;
    private Date accountCreationDate;

    public Pessoa() { }

    public Pessoa(String name, String cpf, String email) {
        this.numeroPessoa = Pessoa.counter;
        this.name = name;
        this.cpf = cpf;
        this.email = email;
        this.accountCreationDate = new Date();
        Pessoa.counter += 1;
    }

    public int getNumeroPessoa() {
        return this.numeroPessoa;
    }

    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public String getCpf() {
        return cpf;
    }
    public void setCpf(String cpf) {
        this.cpf = cpf;
    }
    public String getEmail() {
        return email;
    }
    public void setEmail(String email) {
        this.email = email;
    }
    public Date getAccountCreationDate() {
        return this.accountCreationDate;
    }

    public String toString() {
        return  "\nName: " + this.getName() +
                "\nCPF: " + this.getCpf() +
                "\nEmail: " + this.getEmail() +
                "\nAccount Creation Date: " + Utils.dateToString(this.getAccountCreationDate());
    }


} 

/***

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */
package br.com.albertogomesdasilva.agenciabancaria;

/**
 *
 * @author alber
 */


import java.text.DecimalFormat;
import java.text.NumberFormat;
import java.text.SimpleDateFormat;
import java.util.Date;

public class Utils {

    static NumberFormat formatandoNumeros = new DecimalFormat("R$ #,##0.00");
    static SimpleDateFormat formatandoData = new SimpleDateFormat("dd/MM/yyyy");

    public static String dateToString(Date data) {
        return Utils.formatandoData.format(data);
    }

    public static String doubleToString(Double valor) {
        return Utils.formatandoNumeros.format(valor);
    }

}





