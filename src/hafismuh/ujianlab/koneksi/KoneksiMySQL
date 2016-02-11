/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package hafismuh.ujianlab.koneksi;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

/**
 *
 * @author hafismuh
 */
public class KoneksiMySQL {
    private static Connection koneksi;
    
    public static Connection getKoneksi(){
        if(koneksi == null){
            try{
                
                String url = "jdbc:mysql://localhost:3306/ujianlab2";
                String user = "root";
                String password = "";
                
                DriverManager.registerDriver(new com.mysql.jdbc.Driver());
                koneksi =  DriverManager.getConnection(url, user, password);
            }catch(SQLException ex){
                System.out.println("Error in connection");
            }
        }
        
        return koneksi;
    }
}
