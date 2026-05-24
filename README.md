# Hardcoded stock prices dictionary
stock_prices = {
    "AAPL": 180,
    "TSLA": 250,
    "MSFT": 320,
    "GOOGL": 140
}

# Function to calculate total investment
def stock_tracker():
    total_investment = 0
    portfolio = {}

    while True:
        stock = input("Enter stock symbol (or 'done' to finish): ").upper()
        if stock == "DONE":
            break
        if stock not in stock_prices:
            print("Stock not found in price list.")
            continue
        quantity = int(input(f"Enter quantity of {stock}: "))
        portfolio[stock] = portfolio.get(stock, 0) + quantity
        total_investment += stock_prices[stock] * quantity

    print("\n--- Portfolio Summary ---")
    for stock, qty in portfolio.items():
        print(f"{stock}: {qty} shares @ {stock_prices[stock]} each")
    print(f"Total Investment Value: ${total_investment}")

    # Optionally save to file
    save_choice = input("Save results to file? (y/n): ").lower()
    if save_choice == "y":
        with open("portfolio.txt", "w") as f:
            f.write("--- Portfolio Summary ---\n")
            for stock, qty in portfolio.items():
                f.write(f"{stock}: {qty} shares @ {stock_prices[stock]} each\n")
            f.write(f"Total Investment Value: ${total_investment}\n")
        print("Portfolio saved to portfolio.txt")

# Run the tracker
stock_tracker()

