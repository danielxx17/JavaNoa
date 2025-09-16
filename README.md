Main

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
Controller


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

    package Db;
}
DB


import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class Db {

    private static final String URL = "jdbc:postgresql://ep-shiny-morning-adho75ur-pooler.c-2.us-east-1.aws.neon.tech/neondb";
    private static final String USER = "neondb_owner";
    private static final String PASSWORD = "npg_rt9ewabTZ6Uc";
    private static final String PARAMS = "?sslmode=require&channel_binding=require";

    public static Connection getConnection() throws SQLException {
        try {
            Class.forName("org.postgresql.Driver");
        } catch (ClassNotFoundException e) {
            throw new SQLException("Driver PostgreSQL não encontrado!", e);
        }

        return DriverManager.getConnection(URL + PARAMS, USER, PASSWORD);
    }

}

MODEL


package model;

public class Planta {
    private String nome;
    private String tipoSolo;
    private double quantidadeAgua;
    private double crescimentoEstimado;

    public Planta(String nome, String tipoSolo, double quantidadeAgua, double crescimentoEstimado) {
        this.nome = nome;
        this.tipoSolo = tipoSolo;
        this.quantidadeAgua = quantidadeAgua;
        this.crescimentoEstimado = crescimentoEstimado;
    }

    public String getNome() { return nome; }
    public void setNome(String nome) { this.nome = nome; }

    public String getTipoSolo() { return tipoSolo; }
    public void setTipoSolo(String tipoSolo) { this.tipoSolo = tipoSolo; }

    public double getQuantidadeAgua() { return quantidadeAgua; }
    public void setQuantidadeAgua(double quantidadeAgua) { this.quantidadeAgua = quantidadeAgua; }

    public double getCrescimentoEstimado() { return crescimentoEstimado; }
    public void setCrescimentoEstimado(double crescimentoEstimado) { this.crescimentoEstimado = crescimentoEstimado; }

    public double calcularImpacto() {
        return crescimentoEstimado * (quantidadeAgua / 10);
    }
}
VIEW


import javafx.application.Application;
import javafx.geometry.Insets;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.*;
import javafx.stage.Stage;
import model.Planta;
import controller.PlantaController;

public class PlantasFrontEnd extends Application {

    private TextField nomeField;
    private TextField soloField;
    private TextField aguaField;
    private TextField crescimentoField;
    private TextArea resultadoArea;

    private PlantaController controller = new PlantaController();

    @Override
    public void start(Stage primaryStage) {
        primaryStage.setTitle("Gestão de Plantas");

        VBox mainLayout = new VBox(15);
        mainLayout.setPadding(new Insets(20));
        mainLayout.setAlignment(Pos.CENTER);

        Label titulo = new Label("Cadastro e Análise de Plantas");
        titulo.setStyle("-fx-font-size: 18px; -fx-font-weight: bold;");

        GridPane formulario = criarFormulario();
        HBox botoes = criarBotoes();

        resultadoArea = new TextArea();
        resultadoArea.setEditable(false);
        resultadoArea.setPrefRowCount(10);
        resultadoArea.setStyle("-fx-font-family: monospace;");

        mainLayout.getChildren().addAll(titulo, formulario, botoes, resultadoArea);

        Scene scene = new Scene(mainLayout, 600, 500);
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    private GridPane criarFormulario() {
        GridPane grid = new GridPane();
        grid.setHgap(10);
        grid.setVgap(10);
        grid.setAlignment(Pos.CENTER);

        grid.add(new Label("Nome da Planta:"), 0, 0);
        nomeField = new TextField();
        grid.add(nomeField, 1, 0);

        grid.add(new Label("Tipo de Solo:"), 0, 1);
        soloField = new TextField();
        grid.add(soloField, 1, 1);

        grid.add(new Label("Quantidade de Água (L):"), 0, 2);
        aguaField = new TextField();
        grid.add(aguaField, 1, 2);

        grid.add(new Label("Crescimento Estimado (cm):"), 0, 3);
        crescimentoField = new TextField();
        grid.add(crescimentoField, 1, 3);

        return grid;
    }

    private HBox criarBotoes() {
        HBox box = new HBox(10);
        box.setAlignment(Pos.CENTER);

        Button calcularBtn = new Button("Calcular Impacto");
        calcularBtn.setStyle("-fx-background-color: #4CAF50; -fx-text-fill: white; -fx-font-weight: bold;");
        calcularBtn.setOnAction(e -> calcularImpacto());

        Button limparBtn = new Button("Limpar");
        limparBtn.setStyle("-fx-background-color: #f44336; -fx-text-fill: white; -fx-font-weight: bold;");
        limparBtn.setOnAction(e -> limparCampos());

        box.getChildren().addAll(calcularBtn, limparBtn);
        return box;
    }

    private void calcularImpacto() {
        try {
            String nome = nomeField.getText().trim();
            String solo = soloField.getText().trim();
            double agua = Double.parseDouble(aguaField.getText());
            double crescimento = Double.parseDouble(crescimentoField.getText());

            controller.setPlanta(new Planta(nome, solo, agua, crescimento));
            Planta planta = controller.getPlanta();

            String resultado = String.format(
                "Planta: %s\nTipo de Solo: %s\nÁgua: %.2f L\nCrescimento Estimado: %.2f cm\nImpacto Calculado: %.2f",
                planta.getNome(),
                planta.getTipoSolo(),
                planta.getAgua(),
                planta.getCrescimento(),
                planta.calcularImpacto()
            );

            resultadoArea.setText(resultado);

        } catch (NumberFormatException ex) {
            resultadoArea.setText("Erro: Insira valores numéricos válidos para água e crescimento.");
        } catch (Exception ex) {
            resultadoArea.setText("Erro: " + ex.getMessage());
        }
    }

    private void limparCampos() {
        nomeField.clear();
        soloField.clear();
        aguaField.clear();
        crescimentoField.clear();
        resultadoArea.clear();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
VIEW 

continuacao
package view;

import model.Planta;
import java.util.InputMismatchException;
import java.util.Scanner;

public class PlantaView {
    private Scanner scanner;

    public PlantaView() {
        scanner = new Scanner(System.in);
    }

    public void mostrarInicio() {
        System.out.println("=== Sistema de Gestão de Plantas ===");
    }

    public String lerNome() {
        System.out.print("Digite o nome da planta: ");
        try {
            return scanner.nextLine();
        } catch (Exception e) {
            System.out.println("Erro ao ler o nome.");
            return "";
        }
    }

    public String lerSolo() {
        System.out.print("Digite o tipo de solo: ");
        try {
            return scanner.nextLine();
        } catch (Exception e) {
            System.out.println("Erro ao ler o solo.");
            return "";
        }
    }

    public double lerAgua() {
        System.out.print("Digite a quantidade de água (L): ");
        try {
            return scanner.nextDouble();
        } catch (InputMismatchException e) {
            System.out.println("Valor inválido! Digite um número.");
            scanner.nextLine(); 
            return 0;
        }
    }

    public double lerCrescimento() {
        System.out.print("Digite o crescimento estimado (cm): ");
        try {
            return scanner.nextDouble();
        } catch (InputMismatchException e) {
            System.out.println("Valor inválido! Digite um número.");
            scanner.nextLine();
            return 0;
        }
    }

    public int mostrarMenu() {
        System.out.println("\n=== Menu ===");
        System.out.println("1. Ver dados da planta");
        System.out.println("2. Calcular impacto");
        System.out.println("3. Sair");
        System.out.print("Escolha uma opção: ");
        try {
            int opcao = scanner.nextInt();
            scanner.nextLine(); 
            return opcao;
        } catch (InputMismatchException e) {
            System.out.println("Opção inválida! Digite um número inteiro.");
            scanner.nextLine();
            return -1;
        }
    }

    public void mostrarPlanta(Planta planta) {
        try {
            System.out.println("\n--- Dados da Planta ---");
            System.out.println("Nome: " + planta.getNome());
            System.out.println("Solo: " + planta.getSolo());
            System.out.println("Água: " + planta.getAgua() + " L");
            System.out.println("Crescimento estimado: " + planta.getCrescimento() + " cm");
            System.out.println("Impacto calculado: " + planta.calcularImpacto());
        } catch (Exception e) {
            System.out.println("Erro ao mostrar os dados da planta.");
        }
    }

    public void mostrarMensagem(String mensagem) {
        try {
            System.out.println(mensagem);
        } catch (Exception e) {
            System.out.println("Erro ao exibir a mensagem.");
        }
    }
}

