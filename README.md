# entropy_3

# Viento: Si
viento_si_si <- 3 
viento_si_no <- 3 
viento_si_total <- viento_si_si + viento_si_no

# Viento: No
viento_no_si <- 6
viento_no_no <- 2
viento_no_total <- viento_no_si + viento_no_no

# Función para calcular la entropía
entropy <- function(p) {
  if (p == 0 || p == 1) {
    return(0)
  } else {
    return(-p * log2(p) - (1 - p) * log2(1 - p))
  }
}

# Cálculo de entropía condicionada para Viento
I_viento_si <- entropy(viento_si_si / viento_si_total) 
+ entropy(viento_si_no / viento_si_total)
I_viento_no <- entropy(viento_no_si / viento_no_total) 
+ entropy(viento_no_no / viento_no_total)

# Cálculo de entropía condicionada total para Viento
total_ejemplos <- 14
I_viento <- (viento_si_total / total_ejemplos) * I_viento_si 
+ (viento_no_total / total_ejemplos) * I_viento_no

# Cálculo de Ganancia de Información para Viento
I <- entropy(9/14)  # Entropía del conjunto de datos completo
G_viento <- I - I_viento
