# QUAN LY TUA SACH
package Process;

import Connect.*;
import java.sql.*;
import javax.swing.*;

public class QuanLyTuaSach {
    public static Connection conn = Connect.getConnection();
    public static String sql = null;
    public static PreparedStatement pst = null;
    public static Statement st = null;
    public static void ThemTuaSach(String MaTuaSach, String TenSach, String LoaiSach, String TacGia, String DoTuoi, String SoLuong, String TinhTrang)
    {
        int i=Integer.parseInt(SoLuong);
        sql = "INSERT INTO TUASACH VALUES(?,?,?,?,?,?,?)";
            try 
            {
                pst = conn.prepareStatement(sql);
                pst.setString(1, MaTuaSach);
                pst.setString(2, TenSach);
                pst.setString(3, LoaiSach);
                pst.setString(4, TacGia);
                pst.setString(5, DoTuoi);
                pst.setInt(6, i);
                pst.setString(7, TinhTrang);
                pst.execute();
                JOptionPane.showMessageDialog(null, "Đã thêm tựa sách "+MaTuaSach+" thành công", "Thông báo", 1);
            }
            catch(Exception e)
            {
                JOptionPane.showMessageDialog(null, "Mã tựa sách "+MaTuaSach+" đã tồn tại, vui lòng xem lại dữ liệu", "Thông báo", 1);
            }
    }
    public static void XoaTuaSach(String sqldel)
    {
        sql = "DELETE FROM TUASACH WHERE ";
        sql = sql + sqldel;
        try
        {
            st=conn.createStatement();
            st.execute(sql);
            JOptionPane.showMessageDialog(null, "Đã xóa thành công", "Thông báo", 1);
        }
        catch(Exception e)
        {
            JOptionPane.showMessageDialog(null, "Vui lòng kiểm tra lại các điều kiện cần xóa", "Thông báo", 0);
        }
    }
}
