import streamlit as st

def recommend_product(hair_type, scalp_condition, hair_health, water_type, climate, genetics_history, product_use):
    if scalp_condition == "Dandruff":
        return "Anti-Dandruff Shampoo with Zinc Pyrithione"
    elif scalp_condition == "Oily" and climate in ["Humid", "Hot"]:
        return "Clarifying Shampoo for Oily Scalp"
    elif hair_health == "Damaged" and water_type == "Hard":
        return "Deep Conditioning Hair Mask"
    elif scalp_condition == "Sensitive" or genetics_history == "Yes":
        return "Hypoallergenic Shampoo for Sensitive Skin"
    elif hair_type in ["Curly", "Coily"]:
        return "Leave-In Conditioner for Curly Hair"
    elif hair_health == "Weak" and "Shampoo" in product_use:
        return "Strengthening Conditioner with Biotin"
    elif scalp_condition == "Dry" and climate in ["Hot", "Dry"]:
        return "Coconut Oil Hair Treatment"
    else:
        return "Sulfate-Free Moisturizing Shampoo"

st.title("AI-Powered Hair & Scalp Product Recommendation")

# User Inputs
hair_type = st.selectbox("Select Your Hair Type:", ["Straight", "Wavy", "Curly", "Coily"])
scalp_condition = st.selectbox("Select Your Scalp Condition:", ["Dry", "Oily", "Dandruff", "Sensitive", "Healthy"])
hair_health = st.selectbox("Select Your Hair Health:", ["Healthy", "Moderate", "Damaged", "Weak"])
water_type = st.selectbox("Select Your Water Type:", ["Hard", "Soft"])
climate = st.selectbox("Select Your Climate:", ["Dry", "Humid", "Hot", "Cold"])
genetics_history = st.radio("Do you have a family history of hair loss?", ["Yes", "No"])
product_use = st.multiselect("What hair products do you currently use?", ["Shampoo", "Conditioner", "Oil", "Styling Products", "None"])

# Generate Recommendation
if st.button("Get Recommendation"):
    recommendation = recommend_product(hair_type, scalp_condition, hair_health, water_type, climate, genetics_history, product_use)
    st.success(f"Recommended Product: {recommendation}")
