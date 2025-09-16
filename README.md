package controller;

import model.Planta;
import java.util.InputMismatchException;
import java.util.Scanner;

public class PlantaController {
    private Planta planta;
    private Scanner scanner;

    public PlantaController() {
        scanner = new Scanner(System.in);
    }

    public void cadastrarPlanta() {
        System.out.print("Digite o nome da planta: ");
        String nome = scanner.nextLine();

        System.out.print("Digite o tipo de solo: ");
        String solo = scanner.nextLine();

        double agua = 0;
        while (true) {
            try {
                System.out.print("Digite a quantidade de água (L): ");
                agua = scanner.nextDouble();
                break;
            } catch (InputMismatchException e) {
                System.out.println("Digite um número válido para a água.");
                scanner.nextLine();
            }
        }

        double crescimento = 0;
        while (true) {
            try {
                System.out.print("Digite o crescimento estimado (cm): ");
                crescimento = scanner.nextDouble();
                break;
            } catch (InputMismatchException ) {
                System.out.println("Digite um número válido para o crescimento.");
                scanner.nextLine();
            }
        }

        planta = new Planta(nome, solo, agua, crescimento);
        System.out.println("Planta cadastrada com sucesso!");
    }

    public void exibirPlanta() {
        if (planta != null) {
            System.out.println("\n=== DADOS DA PLANTA ===");
            System.out.println("Nome: " + planta.getNome());
            System.out.println("Tipo de Solo: " + planta.getTipoSolo());
            System.out.println("Água (L): " + planta.getQuantidadeAgua());
            System.out.println("Crescimento Estimado (cm): " + planta.getCrescimentoEstimado());
            System.out.println("Impacto Calculado: " + planta.calcularImpacto());
        } else {
            System.out.println("Nenhuma planta cadastrada.");
        }
    }

    public Planta getPlanta() { return planta; }
    public void setPlanta(Planta planta) { this.planta = planta; }
}


package controller;

import model.Planta;
import java.util.InputMismatchException;
import java.util.Scanner;

public class PlantaController {
    private Planta planta;
    private Scanner scanner;

    public PlantaController() {
        scanner = new Scanner(System.in);
    }

    public void cadastrarPlanta() {
        System.out.print("Digite o nome da planta: ");
        String nome = scanner.nextLine();

        System.out.print("Digite o tipo de solo: ");
        String solo = scanner.nextLine();

        double agua = 0;
        while (true) {
            try {
                System.out.print("Digite a quantidade de água (L): ");
                agua = scanner.nextDouble();
                break;
            } catch (InputMismatchException e) {
                System.out.println("Digite um número válido para a água.");
                scanner.nextLine();
            }
        }

        double crescimento = 0;
        while (true) {
            try {
                System.out.print("Digite o crescimento estimado (cm): ");
                crescimento = scanner.nextDouble();
                break;
            } catch (InputMismatchException ) {
                System.out.println("Digite um número válido para o crescimento.");
                scanner.nextLine();
            }
        }

        planta = new Planta(nome, solo, agua, crescimento);
        System.out.println("Planta cadastrada com sucesso!");
    }

    public void exibirPlanta() {
        if (planta != null) {
            System.out.println("\n=== DADOS DA PLANTA ===");
            System.out.println("Nome: " + planta.getNome());
            System.out.println("Tipo de Solo: " + planta.getTipoSolo());
            System.out.println("Água (L): " + planta.getQuantidadeAgua());
            System.out.println("Crescimento Estimado (cm): " + planta.getCrescimentoEstimado());
            System.out.println("Impacto Calculado: " + planta.calcularImpacto());
        } else {
            System.out.println("Nenhuma planta cadastrada.");
        }
    }

    public Planta getPlanta() { return planta; }
    public void setPlanta(Planta planta) { this.planta = planta; }
}

package controller;

import model.Planta;
import java.util.InputMismatchException;
import java.util.Scanner;

public class PlantaController {
    private Planta planta;
    private Scanner scanner;

    public PlantaController() {
        scanner = new Scanner(System.in);
    }

    public void cadastrarPlanta() {
        System.out.print("Digite o nome da planta: ");
        String nome = scanner.nextLine();

        System.out.print("Digite o tipo de solo: ");
        String solo = scanner.nextLine();

        double agua = 0;
        while (true) {
            try {
                System.out.print("Digite a quantidade de água (L): ");
                agua = scanner.nextDouble();
                break;
            } catch (InputMismatchException e) {
                System.out.println("Digite um número válido para a água.");
                scanner.nextLine();
            }
        }

        double crescimento = 0;
        while (true) {
            try {
                System.out.print("Digite o crescimento estimado (cm): ");
                crescimento = scanner.nextDouble();
                break;
            } catch (InputMismatchException ) {
                System.out.println("Digite um número válido para o crescimento.");
                scanner.nextLine();
            }
        }

        planta = new Planta(nome, solo, agua, crescimento);
        System.out.println("Planta cadastrada com sucesso!");
    }

    public void exibirPlanta() {
        if (planta != null) {
            System.out.println("\n=== DADOS DA PLANTA ===");
            System.out.println("Nome: " + planta.getNome());
            System.out.println("Tipo de Solo: " + planta.getTipoSolo());
            System.out.println("Água (L): " + planta.getQuantidadeAgua());
            System.out.println("Crescimento Estimado (cm): " + planta.getCrescimentoEstimado());
            System.out.println("Impacto Calculado: " + planta.calcularImpacto());
        } else {
            System.out.println("Nenhuma planta cadastrada.");
        }
    }

    public Planta getPlanta() { return planta; }
    public void setPlanta(Planta planta) { this.planta = planta; }
}
