import java.util.Scanner;

public class CurrencyConverter {

    // Static exchange rates relative to 1 USD
    public static double getExchangeRate(String from, String to) {
        // Example static rates
        double usdToInr = 83.0;
        double usdToEur = 0.91;
        double usdToGbp = 0.78;

        double fromRate = 1.0, toRate = 1.0;

        switch (from.toUpperCase()) {
            case "USD": fromRate = 1.0; break;
            case "INR": fromRate = 1 / usdToInr; break;
            case "EUR": fromRate = 1 / usdToEur; break;
            case "GBP": fromRate = 1 / usdToGbp; break;
            default:
                System.out.println("Unsupported base currency.");
                return -1;
        }

        switch (to.toUpperCase()) {
            case "USD": toRate = 1.0; break;
            case "INR": toRate = usdToInr; break;
            case "EUR": toRate = usdToEur; break;
            case "GBP": toRate = usdToGbp; break;
            default:
                System.out.println("Unsupported target currency.");
                return -1;
        }

        return fromRate * toRate;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Currency Converter");
        System.out.print("Enter base currency (USD, INR, EUR, GBP): ");
        String baseCurrency = scanner.nextLine();

        System.out.print("Enter target currency (USD, INR, EUR, GBP): ");
        String targetCurrency = scanner.nextLine();

        System.out.print("Enter amount to convert: ");
        double amount = scanner.nextDouble();

        double rate = getExchangeRate(baseCurrency, targetCurrency);
        if (rate == -1) {
            System.out.println("Conversion failed due to unsupported currency.");
        } else {
            double converted = amount * rate;
            System.out.printf("Converted amount: %.2f %s\n", converted, targetCurrency.toUpperCase());
        }

        scanner.close();
    }
}
