import streamlit as st

st.title("Simple Calculator 🔢")

st.write("Choose an operation and enter numbers below:")

menu = st.selectbox(
    "Choose an option:",
    (1, 2, 3, 4, 5),
    format_func=lambda x: {
        1: "1. Addition",
        2: "2. Subtraction",
        3: "3. Multiplication",
        4: "4. Division",
        5: "5. Exit",
    }[x]
)

if menu == 5:
    st.warning("Exiting... Thank you!")
    st.stop()

# Number inputs appear only when a valid operation is chosen
num1 = st.number_input("Enter the first number:", value=0.0)
num2 = st.number_input("Enter the second number:", value=0.0)

if st.button("Calculate"):
    if menu == 1:
        result = num1 + num2
        st.success(f"The addition of {num1} and {num2} is: {result}")

    elif menu == 2:
        if num1 > num2:
            result = num1 - num2
            st.success(f"The subtraction of {num1} and {num2} is: {result}")
        else:
            result = num2 - num1
            st.success(f"The subtraction of {num2} and {num1} is: {result}")

    elif menu == 3:
        result = num1 * num2
        st.success(f"The multiplication of {num1} and {num2} is: {result}")

    elif menu == 4:
        if num2 == 0:
            st.error("Division by zero is not possible. Try another number.")
        else:
            result = num1 / num2
            st.success(f"The division of {num1} and {num2} is: {result}")
