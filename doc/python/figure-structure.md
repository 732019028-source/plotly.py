import plotly.express as px

# Membuat dataframe dari hasil regresi di dokumen
df_regresi = pd.DataFrame({
    "Variabel Dependen": ["Abnormal Return (AR)", "Market Capitalization"],
    "Koefisien": [0.138095, -1.97e+10],
    "Std. Error": [0.222513, 7.19e+09],
    "t-Statistik": [0.620615, -2.741673],
    "Probabilitas": [0.5350, 0.0062]
})

# Kita ubah dataframe menjadi format long agar mudah divisualkan dengan plotly express
df_long = df_regresi.melt(id_vars="Variabel Dependen", 
                          value_vars=["Koefisien", "Std. Error", "t-Statistik", "Probabilitas"],
                          var_name="Indikator",
                          value_name="Nilai")

# Membuat visualisasi interaktif line chart
fig = px.line(df_long, 
              x="Indikator", 
              y="Nilai", 
              color="Variabel Dependen", 
              markers=True,
              title="Visualisasi Hasil Regresi untuk Setiap Indikator")

fig.show()
