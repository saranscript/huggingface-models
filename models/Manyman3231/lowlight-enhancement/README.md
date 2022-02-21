   return im


def main():
    st.title("Lowlight Enhancement")
    st.write("This is a simple lowlight enhancement app with great performance and does not require paired images to train.")
    st.write("The model runs at 1000/11 FPS on single GPU/CPU on images with a size of 1200*900*3")
    uploaded_file = st.file_uploader("Lowlight Image")
    if uploaded_file:
        data_lowlight = Image.open(uploaded_file)
        col1, col2 = st.columns(2)
        col1.write("Original (Lowlight)")
        col1.image(data_lowlight, caption="Lowlight Image", use_column_width=True)
