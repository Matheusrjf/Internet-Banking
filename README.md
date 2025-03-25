import java.util.Scanner;

// Classe para representar a conta bancária
class ContaBancaria {
    private String agencia;
    private String conta;
    private double saldo;

    // Construtor para inicializar a conta com valores padrão
    public ContaBancaria(String agencia, String conta) {
        this.agencia = agencia;
        this.conta = conta;
        this.saldo = 0.0; // saldo inicial zerado
    }

    // Método para depositar dinheiro na conta
    public void depositar(double valor) {
        this.saldo += valor;
        System.out.println("Depósito de R$" + valor + " realizado com sucesso.");
    }

    // Método para sacar dinheiro da conta
    public void sacar(double valor) {
        if (valor > this.saldo) {
            System.out.println("Saldo insuficiente para realizar saque.");
        } else {
            this.saldo -= valor;
            System.out.println("Saque de R$" + valor + " realizado com sucesso.");
        }
    }

    // Método para verificar o saldo disponível na conta
    public double verificarSaldo() {
        return this.saldo;
    }

    // Método para mostrar informações da conta
    public void mostrarInfoConta() {
        System.out.println("----- Informações da Conta -----");
        System.out.println("Agência: " + this.agencia);
        System.out.println("Conta: " + this.conta);
        System.out.println("Saldo disponível: R$" + this.saldo);
        System.out.println("--------------------------------");
    }
}

// Classe principal que contém o programa
public class ProgramaContaBancaria {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Solicitar dados da agência e conta para o cliente
        System.out.println("Digite o número da agência:");
        String agencia = scanner.nextLine();

        System.out.println("Digite o número da conta:");
        String conta = scanner.nextLine();

        // Criar uma instância da ContaBancaria
        ContaBancaria minhaConta = new ContaBancaria(agencia, conta);

        // Menu de interação com o usuário
        int opcao;
        do {
            System.out.println("\n----- Menu -----");
            System.out.println("1. Depositar");
            System.out.println("2. Sacar");
            System.out.println("3. Verificar Saldo");
            System.out.println("4. Mostrar Informações da Conta");
            System.out.println("0. Sair");
            System.out.println("Escolha uma opção:");

            opcao = scanner.nextInt();
            double valor;

            switch (opcao) {
                case 1:
                    System.out.println("Digite o valor a depositar:");
                    valor = scanner.nextDouble();
                    minhaConta.depositar(valor);
                    break;
                case 2:
                    System.out.println("Digite o valor a sacar:");
                    valor = scanner.nextDouble();
                    minhaConta.sacar(valor);
                    break;
                case 3:
                    System.out.println("Saldo disponível: R$" + minhaConta.verificarSaldo());
                    break;
                case 4:
                    minhaConta.mostrarInfoConta();
                    break;
                case 0:
                    System.out.println("Saindo...");
                    break;
                default:
                    System.out.println("Opção inválida. Tente novamente.");
                    break;
            }

        } while (opcao != 0);

        scanner.close();
    }
}
