import java.util.;

class Covek {
    private String name;

    public void setName(String name) { this.name = name; }
    public String getName() { return name; }
    public String toString() { return name; }
}

class Ocena {
    private int vrednost;
    private String datum;
    private String predmet;
    public void setOcena(int vrednost, String datum, String predmet) {
        this.vrednost = vrednost;
        this.datum = datum;
        this.predmet = predmet;
    }

    public int getVrednost() { return vrednost; }
    public String getDatum() { return datum; }
    public String getPredmet() { return predmet; }

    public String toString() {
        return datum + " " + predmet + " " + String.valueOf(vrednost);
    }
}

class Student extends Covek {
    private String indeks;
    private Ocena ocenki [] = new Ocena[100];
    private int num = 0;

    public void setIndeks(String indeks) { this.indeks = indeks; }
    public String getIndeks() { return indeks; }
    public void setOcena(Ocena o) {
        System.out.println("Vmetnata ocena: " + o.toString());
        ocenki[num] = o;
        num++;
    }

    public float getProsek(){
        int total = 0;
        for (int i = 0; i < num; i++){
            total = total + ocenki[i].getVrednost();
        }
        return (float) total / num;
    }

    public String toString() {
        return this.getName() + " " + indeks + " " + String.valueOf(getProsek());
    }
}

public class Main
{
    public static void main(String[] args) {
        Student Naum = new Student();
        Naum.setIndeks("INKI 756");
        Naum.setName("Naum Trpezanovski");

        Ocena oop = new Ocena();
        oop.setOcena(10, "2021-11-04 15:12:32", "Digitalni Sistemi");
        Naum.setOcena(oop);

        Ocena sp = new Ocena();
        sp.setOcena(9, "2021-11-01 10:22:05", "Matematika 1");
        Naum.setOcena(sp);

        System.out.println(Naum.toString());
    }
}
