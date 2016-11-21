# Agenda
//Création d'une agenda en java ..
/*Il vous faux quatre classes 
les classes comme suit (date, event, proprietaire, Agenda )
*/
class date {
        int j; int m; int a;
        date(int x, int y, int z){ j=x ; m = y ; a = z;}
        date(){j=1; m=1; a=2000; }       
        date(date x){j=x.j; m=x.m; a=x.a; }
        boolean Equal(date d){ return d.j == j && d.m == m && d.a == a ;}
        boolean plusrecente(date d){return this.j + this.m*100 + this.a*1000 > d.j + d.m*10 + d.a*1000;}
        String FormatStr(){return String.valueOf(j)+"/"+String.valueOf(m)+"/"+String.valueOf(a);}
        void show(){System.out.println(FormatStr());}
        void saisie(){j = Integer.parseInt(JOptionPane.showInputDialog(null,"jour"));
                       m = Integer.parseInt(JOptionPane.showInputDialog(null,"Mois"));
                        a = Integer.parseInt(JOptionPane.showInputDialog(null,"Annee"));}
}
class even {
        String libE; date dateE; int priE;
        even(){libE=""; dateE=new date(); priE=1;}
        even(String lib, date d, int p ){libE=lib ; dateE=new date(d); priE=p;}
        void show(){System.out.println(this.libE+" "+this.dateE.FormatStr()+" "+String.valueOf(priE));}
        void modifierdate(date nouvdate){dateE=nouvdate;} 
        void listerEvenDate(even[] T, int n, date d ) {
            System.out.println("Lister Even a la date "+d.FormatStr()); 
            for( int i = 0; i < n; i++)
            {
                if (T[i].dateE.Equal(d) == true)
                    T[i].show();
        
                }
        }
        void listerevenpri(even[] T, int n, int p){
        System.out.println("Lister Even de Pri "+p);
        for( int i = 0; i < n; i++){
            if(T[i].priE == p)
                T[i].show();
            }
        }
        even PlusRecent(even e){
            if (this.dateE.plusrecente(e.dateE))
                return this ;
            else 
                return e;
        }
    }
    class agenda {
        
        even[] Teven;
        int anneeA ; String propA;
        static final String Auteur="Montassar";
        static final date DCC = new date(20,10,2016);
        static int nbAg = 0;
        static date DMC;
        agenda(String prop, int annee){
        propA = prop;
        anneeA = annee;
        Teven = new even[100];
        for (int i = 0; i < 100 ; i++)
            Teven[i] = new even();                       
        nbAg++;        
        }
        agenda(String prop, int annee, int nbE){
        propA = prop;
        anneeA = annee;
        Teven = new even[nbE];
        for (int i = 0; i < nbE ; i++)
            Teven[i] = new even();                       
        nbAg++;        
        }
        void show(){            
            for ( int i = 0; i < Teven.length; i++)
                Teven[i].show();    
        }        
        void listerunedate(date d){
            System.out.println("lister une date : "+d.FormatStr());
            for( int i = 0; i < 3; i++)
                {
                    if (Teven[i].dateE.Equal(d) == true)
                         Teven[i].show();        
                }
        }
        void charger(){
            JOptionPane.showMessageDialog(null,"Saisi D'agenda");
            for( int i =0 ; i<Teven.length; i++)
                {
                   String lib = JOptionPane.showInputDialog("Dooner  lib : ");
                   if(lib.isEmpty())return;
                   date d = new date(); d.saisie();
                   int pri = Integer.parseInt(JOptionPane.showInputDialog(null,"Donner Pri"));
                   Teven[i] = new even(lib,d,pri); 
                }
            DMC = new date(03,11,2016);
            
        }
        void listerevenprio(int p){
            System.out.println("Lister Even de Pri "+p);
            for( int i = 0; i < Teven.length; i++){
                if(Teven[i].priE == p)
                    Teven[i].show();
            }
        }
        static int getnbAg(){
            return nbAg;
        }
        
}
