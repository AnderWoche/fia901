=====================
Anwendungsentwicklung
=====================

Unterrichtet von Herrn Katzberg

#####################
MSSQL Server Anbindung in Java
#####################

.. code-block:: java

 import java.sql.*;

 public class MSSQL_Java {
    public static void main(String[]  args) throws ClassNotFoundException {

        Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");

        String connectionURL = "jdbc:sqlserver://localhost:1434;databaseName=TestDB;integratedSecurity=true;";

        try(Connection connection = DriverManager.getConnection(connectionURL)) {

            Statement statement = connection.createStatement();

            String sql = "SELECT * FROM dbo.T_PERSON";
            ResultSet resultSet = statement.executeQuery(sql);

            while(resultSet.next()) {
                System.out.println(resultSet.getString("NAME") + " : " + resultSet.getString("Nachname"));
            }

        } catch (SQLException throwable) {
            throwable.printStackTrace();
        }
    }
 }
..

**********************
SQL Joints
**********************

Joints Macht Beziehungen
Mit Joint kann man ein select begehl so umbauen das es tabelen mit einadner vereint
so kriegt man ergenisse (daten) aus mehreren tabellen.
mit joints benutzet man aktiv primar und secundar schlüssel
Joint nutzen die beziehujgen der tabbeln aktiv

.. content-tabs::

    .. tab-container:: tab1
        :title: Tab title one

        Content for tab one

    .. tab-container:: tab2
        :title: Tab title two

        Content for tab two

1 Kunden der keine reservieung hat
2 Kunden die eine reservierung haben
3 Reservierung, die keine kunden haben (zu geordnet ist)

Innerjoin oder naturaljoin
SELECT * FROM Kunden, Reservierung WEHRE Kunden.KdNr = Reservierung.KdNr;
SELECT * FROM Kunden INNER JOIN Reservierung ON Kunden.KdNr = Reservierung.KdNr

1 Left Outer Join
1 + 2 Left Join
2 + 3 Right Join
2 Right Outer Join

