# 🛍️ Heritage — Gestione Catalogo Prodotti

Progetto Java che modella un negozio con catalogo di prodotti fisici e digitali.
Sviluppato nell'ambito del percorso IFTS DevOps – IFOA Milano.

---

## 📋 Descrizione

Heritage simula la gestione di un **negozio** (`Store`) con un catalogo di prodotti (`Product`).
I prodotti possono essere di due tipi:
- **Fisici** (`PhysicalProduct`) — con dimensioni e peso
- **Digitali** (`DownloadableProduct`) — con peso in MB e URL di download

Il sistema gestisce l'inserimento nel catalogo evitando duplicati, e offre metodi di analisi come il calcolo del prezzo medio, il prodotto più economico e il conteggio dei prodotti sotto media.

---

## 🗂️ Struttura del progetto

```
heritage/
├── pom.xml
└── src/
    └── main/
        └── java/
            └── com/mycompany/heritage/
                ├── Heritage.java                        # Entry point (main)
                ├── Product.java                         # Classe base prodotto
                ├── PhysicalProduct.java                 # Prodotto fisico
                ├── DownloadableProduct.java             # Prodotto digitale
                ├── Store.java                           # Gestione catalogo
                └── exceptions/
                    ├── ProductAlreadyPresentException.java
                    └── ProductNotInsertableException.java
```

---

## 🧱 Classi principali

### `Product`
Classe base per tutti i prodotti del catalogo.

| Proprietà     | Tipo     | Descrizione              |
|---------------|----------|--------------------------|
| `name`        | `String` | Nome del prodotto        |
| `description` | `String` | Descrizione              |
| `price`       | `float`  | Prezzo                   |

---

### `PhysicalProduct` *(extends Product)*
Prodotto con caratteristiche fisiche di spedizione.

| Proprietà | Tipo    | Descrizione  |
|-----------|---------|--------------|
| `weight`  | `float` | Peso (kg)    |
| `width`   | `float` | Larghezza    |
| `height`  | `float` | Altezza      |
| `depth`   | `float` | Profondità   |

---

### `DownloadableProduct` *(extends Product)*
Prodotto digitale scaricabile.

| Proprietà | Tipo     | Descrizione               |
|-----------|----------|---------------------------|
| `size`    | `float`  | Dimensione file (MB)      |
| `url`     | `String` | URL per il download       |

---

### `Store`
Gestisce il catalogo prodotti con un array dinamico.

| Metodo | Descrizione |
|--------|-------------|
| `AddProduct(Product)` | Aggiunge un prodotto (lancia eccezione se già presente o null) |
| `indexOf(String)` | Restituisce la posizione del prodotto per nome (-1 se assente) |
| `getCheapestProduct()` | Restituisce il prodotto meno costoso (null se catalogo vuoto) |
| `getAvgPrice()` | Calcola il prezzo medio del catalogo |
| `countProductBelowAvg()` | Conta i prodotti con prezzo sotto la media |
| `countDownloadableProduct()` | Conta i prodotti di tipo `DownloadableProduct` |

**Logica di inserimento:** il catalogo viene espanso dinamicamente con `System.arraycopy` — ad ogni inserimento valido viene creato un nuovo array di lunghezza `n+1`.

---

## ⚠️ Eccezioni

| Eccezione | Quando viene lanciata |
|-----------|-----------------------|
| `ProductAlreadyPresentException` | Un prodotto con lo stesso nome è già nel catalogo |
| `ProductNotInsertableException`  | Prodotto non inseribile (già presente o riferimento null) |

---

## 🏗️ Gerarchia delle classi

```
Product
├── PhysicalProduct
└── DownloadableProduct

Store
└── usa Product[]
```

---

## 🚀 Requisiti e build

- **Java** 25+
- **Maven** 3.x

```bash
# Clona il progetto
git clone https://github.com/lylian-devops/heritage.git
cd heritage

# Compila
mvn compile

# Esegui
mvn exec:java

# Package
mvn package
```

---

## 🛠️ Tecnologie

- Java 25 (OOP, ereditarietà, eccezioni custom, `instanceof`)
- Maven (build & dependency management)
- NetBeans (IDE di sviluppo)

---

## 👤 Autore

**Lylian Harding** — DevOps Trainee  
🔗 [github.com/lylian-devops](https://github.com/lylian-devops)

---

*Progetto sviluppato nell'ambito del corso IFTS DevOps – IFOA, Milano (2025)*
