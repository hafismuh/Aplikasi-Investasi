/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package hafismuh.ujianlab.app;

import hafismuh.latihan.koneksi.KoneksiMySQL;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import javax.swing.table.DefaultTableModel;

/**
 *
 * @author hafismuh
 */
public final class FormApp extends javax.swing.JFrame {
    private final DefaultTableModel model;
    

    /**
     * Creates new form PegawaiApp
     */
    public FormApp() {
        initComponents();
        setLocationRelativeTo(this);
        model = new DefaultTableModel();
        
        jTableTransaksi.setModel(model);
        model.addColumn("No Kontrak");
        model.addColumn("Tgl Kontrak");
        model.addColumn("Kode Investor");
        model.addColumn("Nama Investor");
        model.addColumn("Kode Investasi");
        model.addColumn("Nama Investasi");
        model.addColumn("Jenis Investasi");
        model.addColumn("Modal");
        model.addColumn("Bunga");
        model.addColumn("Total");
        
        jComboBoxKdInvestasi.setSelectedIndex(-1);
        loadData();
    }
    
    public void loadData(){
        model.getDataVector().removeAllElements();
        model.fireTableDataChanged();
        
        try{
            Connection c = KoneksiMySQL.getKoneksi();
            Statement s = c.createStatement();
            
            String sql = "SELECT * FROM tb_transaksi";
            ResultSet rs = s.executeQuery(sql);
            while(rs.next()){
                Object [] o = new Object[10];
                o [0] = rs.getString("no_kontrak");
                o [1] = rs.getDate("tgl_trans");
                o [2] = rs.getString("kode_investor");
                o [3] = rs.getString("nama_investor");
                o [4] = rs.getString("kode_investasi");
                o [5] = rs.getString("nama_investasi");
                o [6] = rs.getString("jns_investasi");
                o [7] = rs.getInt("modal");
                o [8] = rs.getInt("bunga");
                o [9] = rs.getInt("total");
                model.addRow(o);
            }
            s.close();
            rs.close();
        }catch(SQLException ex){
            System.out.println("Gagal Load Data");
        }
    }
    
    public void hitungBunga(){
        int bunga = 0;
        int total = 0;
        
        if(jR1.isSelected()){
            int modal = Integer.parseInt(jTextFieldModal.getText());
            jTextFieldBunga.setText(String.valueOf(bunga));
            jTextFieldTotal.setText(String.valueOf(total));
            bunga = modal * 10 / 100;
            total = modal - bunga;
        }else if(jR2.isSelected()){
            int modal = Integer.parseInt(jTextFieldModal.getText());
            jTextFieldBunga.setText(String.valueOf(bunga));
            jTextFieldTotal.setText(String.valueOf(total));
            bunga = modal * 15 / 100;
            total = modal - bunga;
        }else if(jR3.isSelected()){
            int modal = Integer.parseInt(jTextFieldModal.getText());
            jTextFieldBunga.setText(String.valueOf(bunga));
            jTextFieldTotal.setText(String.valueOf(total));
            bunga = modal * 20 / 100;
            total = modal - bunga;
        }
        jTextFieldBunga.setText(String.valueOf(bunga));
        jTextFieldTotal.setText(String.valueOf(total));
    }
    
    private void jButtonTambahActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jButtonTambahActionPerformed
        // TODO add your handling code here:
        
        String no_kontrak = jTextFieldNoKontrak.getText();
        java.util.Date tgl_trans = (java.util.Date)jFormattedTglTx.getValue();
        String kd_investor = jTextFieldKdInvestor.getText();
        String nm_investor = jTextFieldNmInvestor.getText();
        String kd_investa = (String) jComboBoxKdInvestasi.getSelectedItem();
        String nm_investa = jTextFieldNmInvestasi.getText();
        String jns_investa = jTextFieldJnsInvestasi.getText();
        int modal = Integer.valueOf(jTextFieldModal.getText());
        int bunga = Integer.valueOf(jTextFieldBunga.getText());
        int total = Integer.valueOf(jTextFieldTotal.getText());
       
        try{
            Connection c = KoneksiMySQL.getKoneksi();
            
            String sql = "INSERT INTO tb_transaksi values (?, ?, ?, ?, ?, ?, ?, ?, ?, ?)";
            
            PreparedStatement p = c.prepareStatement(sql);
            
            p.setString(1, no_kontrak);
            p.setDate(2, new java.sql.Date(tgl_trans.getTime()));
            p.setString(3, kd_investor);
            p.setString(4, nm_investor);
            p.setString(5, kd_investa);
            p.setString(6, nm_investa);
            p.setString(7, jns_investa);
            p.setInt(8, modal);
            p.setInt(9, bunga);
            p.setInt(10, total);
            p.executeUpdate();
            p.close();
        }catch(SQLException ex){
            System.out.println("Gagal Menyimpan");
        }finally{
            loadData();
        }
        
    }//GEN-LAST:event_jButtonTambahActionPerformed

    private void jTextFieldNmInvestasiActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jTextFieldNmInvestasiActionPerformed
        // TODO add your handling code here:
    }//GEN-LAST:event_jTextFieldNmInvestasiActionPerformed

    private void jR1ActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jR1ActionPerformed
        // TODO add your handling code here:
        hitungBunga();
    }//GEN-LAST:event_jR1ActionPerformed

    private void jR2ActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jR2ActionPerformed
        // TODO add your handling code here:
        hitungBunga();
    }//GEN-LAST:event_jR2ActionPerformed

    private void jR3ActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jR3ActionPerformed
        // TODO add your handling code here:
        hitungBunga();
    }//GEN-LAST:event_jR3ActionPerformed

    private void jComboBoxKdInvestasiActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jComboBoxKdInvestasiActionPerformed
        // TODO add your handling code here:
        String nm_investa = null;
        String jns_investa = null;
        int modal = 0;

        if("K-001".equals(jComboBoxKdInvestasi.getSelectedItem())){
            nm_investa = "MODAL ASING";
            jns_investa = "Investasi Asing";
            modal = 7000000;
        }else if("K-002".equals(jComboBoxKdInvestasi.getSelectedItem())){
            nm_investa = "SAHAM BERJANGKA";
            jns_investa = "Dalam Negeri";
            modal = 8000000;
        }else if("K-003".equals(jComboBoxKdInvestasi.getSelectedItem())){
            nm_investa = "BURSA SAHAM";
            jns_investa = "Dalam Negeri";
            modal = 9000000;
        }
        jTextFieldNmInvestasi.setText(nm_investa);
        jTextFieldJnsInvestasi.setText(jns_investa);
        jTextFieldModal.setText(String.valueOf(modal));
        
    }

    private void jTableTransaksiMouseClicked(java.awt.event.MouseEvent evt) {//GEN-FIRST:event_jTableTransaksiMouseClicked
        // TODO add your handling code here:
        int i = jTableTransaksi.getSelectedRow();
        if(i == -1){
            return;
        }
        String no_kontrak = (String) jTableTransaksi.getValueAt(i, 0);
        jTextFieldNoKontrak.setText(no_kontrak);
        
        java.util.Date tgl_trans = (java.util.Date) jTableTransaksi.getValueAt(i, 1);
        jFormattedTglTx.setValue(tgl_trans);
        
        String kd_investor = (String) jTableTransaksi.getValueAt(i, 2);
        jTextFieldKdInvestor.setText(kd_investor);
        
        String nm_investor = (String) jTableTransaksi.getValueAt(i, 3);
        jTextFieldNmInvestor.setText(nm_investor);
        
        String kd_investa = (String) jTableTransaksi.getValueAt(i, 4);
        jComboBoxKdInvestasi.setSelectedItem(kd_investa);
        
        String nm_investa = (String) jTableTransaksi.getValueAt(i, 5);
        jTextFieldNmInvestasi.setText(nm_investa);
        
        String jns_investa = (String) jTableTransaksi.getValueAt(i, 6);
        jTextFieldJnsInvestasi.setText(jns_investa);
        
        int modal = (Integer) jTableTransaksi.getValueAt(i, 7);
        jTextFieldModal.setText(String.valueOf(modal));
        
        int bunga = (Integer) jTableTransaksi.getValueAt(i, 8);
        jTextFieldBunga.setText(String.valueOf(bunga));
        
        int total = (Integer) jTableTransaksi.getValueAt(i, 9);
        jTextFieldTotal.setText(String.valueOf(total));
    }

    private void jButtonUbahActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jButtonUbahActionPerformed
        // TODO add your handling code here:
        int i = jTableTransaksi.getSelectedRow();
        if(i == -1){
            return;
        }
        
        String no_kontrak = (String) model.getValueAt(i, 0);
        
        java.util.Date tgl_trans = (java.util.Date)jFormattedTglTx.getValue();
        String kd_investor = jTextFieldKdInvestor.getText();
        String nm_investor = jTextFieldNmInvestor.getText();
        String kd_investa = (String) jComboBoxKdInvestasi.getSelectedItem();
        String nm_investa = jTextFieldNmInvestasi.getText();
        String jns_investa = jTextFieldJnsInvestasi.getText();
        int modal = Integer.valueOf(jTextFieldModal.getText());
        int bunga = Integer.valueOf(jTextFieldBunga.getText());
        int total = Integer.valueOf(jTextFieldTotal.getText());
       
        try{
            Connection c = KoneksiMySQL.getKoneksi();
            
            String sql = "UPDATE tb_transaksi SET tgl_trans = ?, kode_investor = ?, nama_investor = ?, kode_investasi = ?, nama_investasi = ?,"
                    + " jns_investasi = ?, modal = ?, bunga = ?, total = ? WHERE no_kontrak = ?)";
            
            PreparedStatement p = c.prepareStatement(sql);
            
            p.setDate(1, new java.sql.Date(tgl_trans.getTime()));
            p.setString(2, kd_investor);
            p.setString(3, nm_investor);
            p.setString(4, kd_investa);
            p.setString(5, nm_investa);
            p.setString(6, jns_investa);
            p.setInt(7, modal);
            p.setInt(8, bunga);
            p.setInt(9, total);
            p.setString(10, no_kontrak);
            p.executeUpdate();
            p.close();
        }catch(SQLException ex){
            System.out.println("Gagal Mengubah");
        }finally{
            loadData();
        }
    }

    private void jButtonHapusActionPerformed(java.awt.event.ActionEvent evt) {//GEN-FIRST:event_jButtonHapusActionPerformed
        // TODO add your handling code here:
        int i = jTableTransaksi.getSelectedRow();
        if(i == -1){
            return;
        }
        
        String no_kontrak = (String) model.getValueAt(i, 0);
       
        try{
            Connection c = KoneksiMySQL.getKoneksi();
            
            String sql = "DELETE * FROM tb_transaksi WHERE no_kontrak = ?)";
            
            PreparedStatement p = c.prepareStatement(sql);
            
            p.setString(1, no_kontrak);
            p.executeUpdate();
            p.close();
        }catch(SQLException ex){
            System.out.println("Gagal Menghapus");
        }finally{
            loadData();
        }
    }

        /* Create and display the form */
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new FormApp().setVisible(true);
                
                
            }
        });
    }
