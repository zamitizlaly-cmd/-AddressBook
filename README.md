package addressbook;

import java.io.*;
import java.util.*;

public class Directorio {
    private Map<String, String> contactos;

    public Directorio() {
        contactos = new HashMap<>();
    }

    // Cargar contactos desde archivo CSV
    public void load() {
        try (BufferedReader br = new BufferedReader(new FileReader("contactos.txt"))) {
            String linea;
            while ((linea = br.readLine()) != null) {
                String[] partes = linea.split(",");
                if (partes.length == 2) {
                    contactos.put(partes[0], partes[1]);
                }
            }
            System.out.println("Contactos cargados correctamente.");
        } catch (IOException e) {
            System.out.println("No se pudo cargar el archivo de contactos
