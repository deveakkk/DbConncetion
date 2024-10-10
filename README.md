import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public  class DbConnectionImpl implements DbConnection {
    @Override
    public void select() {
        try {
            var request = "SELECT * FROM public.products";
            Statement statement = connect().createStatement();
            ResultSet resultSet = statement.executeQuery(request);

            while (resultSet.next()) {
                var id = resultSet.getLong("id");
                var modelName = resultSet.getString("product_name");
                var price = resultSet.getDouble("price");

                System.out.println("ID -" + id + ", model - " + modelName + ", price -" + price);
            }
        } catch (SQLException e) {
            System.out.println("Cannot load data from db. Please try again.");

            }
        }

    @Override
    public void insert() {

    }

    @Override
    public void update() {

    }

    @Override
    public void delete() {

    }

}
