
# Automatic Machine Learning Introduction with Driverless AI

## Outline

- [Objective](#objective)
- [Prerequisites](#prerequisites)
- [Task 1: Product Tour](#task-1-product-tour)
- [Task 2: Automatic Machine Learning Concepts](#task-2-automatic-machine-learning-concepts)
- [Task 3: Load Data](#task-3-load-data)
- [Task 4: Explore Data Details and AutoViz](#task-4-explore-data-details-and-autoviz)
- [Task 5: Launch First Experiment](#task-5-launch-first-experiment)
- [Task 6: Explore Feature Engineering](#task-6-explore-feature-engineering)
- [Task 7: Explore Experiment Results](#task-7-explore-experiment-results)
- [Task 8: MLI Report for Non-Time-Series](#task-8-mli-report-for-non-time-series)
- [Task 9: Experiment Summary and Autoreport](#task-9-experiment-summary-and-autoreport)
- [Next Steps](#next-steps)
- [Appendix: Project Workspace](#appendix-project-workspace)


## Objectivo

Para este tutorial, vamos a explorar el conjunto de datos sobre el Titanic desde la perspectiva de una compañía de aseguranza de vidas usando el producto de empresa de [H2O.ai](https://www.h2o.ai/), [Driverless AI](https://www.h2o.ai/products/h2o-driverless-ai/). Vamos a explorar posibles factores de riesgos derivados desde este conjunto de datos que la compañía podría haber considerado al momento de vender aseguranza de vida a estos pasajeros. Específicamente, crearemos un modelo de predicción para determinar cuales factores contribuyeron a la supervivencia de los pasajeros.

En este tutorial de Driverless AI, vamos a aprender a cargar datos, explorar detalles sobre los datos, generar auto-visualizaciones, lanzar un experimento, explorar feature engineering, desplegar los resultados del experimento, y daremos un pequeño tour del reporte de Machine Learning Interpretability.

**Nota**: Este tutorial ha sido creado en Aquarium, lo cual es parte de H2O cloud y provee acceso a varias herramientas para talleres, conferencias, y entrenamientos de enseñanza. Los laboratorios en Aquarium tienen conjuntos de datos, experimentos, proyectos, y otros contenidos precargados. Si usted usa su propia versión de Driverless AI, no podrá ver el contenido precargado.


## Prerequisites

A **Two Hour Test Drive session**: Test Drive is H2O's Driverless AI on the AWS Cloud. No need to download software. Explore all the features and benefits of the H2O Automatic Learning Platform. 

- Need a **Two Hour Test Drive** session? [Try it Now](https://www.h2o.ai/test-drive/). Follow the instructions [on this quick tutorial](https://h2oai.github.io/tutorials/getting-started-with-driverless-ai-test-drive/#0) to get a Test Drive session started. After the Driverless AI Test Drive session starts, continue reading the remaining prerequisites of this tutorial then start [Task 1: Product Tour](https://h2oai.github.io/tutorials/automatic-ml-intro-test-drive-tutorial/#2).

- Already have a **Two Hour Test Drive** session? Continue reading the remaining prerequisites of this tutorial then start [Task 1: Product Tour](https://h2oai.github.io/tutorials/automatic-ml-intro-test-drive-tutorial/#2). 

**Note: Each Test Drive instance will be available to you for two hours, after which it will terminate. No work will be saved. If you need more time to further explore Driverless AI, you can always launch another Test Drive instance or reach out to our sales team via the [contact us form](https://www.h2o.ai/company/contact/).**

- Basic knowledge of Machine Learning and Statistics


## Task 1: Product Tour

Welcome to the Driverless AI **Datasets** page! 

![dai-datasets-page](assets/dai-datasets-page.jpg)

The Driverless UI is easy to navigate. The following features, as well as a few datasets, are found on the **Datasets** page. We will explore these features as we launch an experiment in the next tasks.

1. **Projects**: Projects Workspace for managing datasets and experiments menu option.

2. **Datasets**: View of current datasets. Other features for datasets include the options to add a dataset, get dataset details, visualize, split, predict, rename, download, and delete. 

3. **Autoviz**: Visualize a dataset with all available graphs.

4. **Experiments**: View of completed experiments. Experiments can be revised or deleted. 

5. **Diagnostics**: Diagnose a model and view model performance for multiple scorers based on the existing model and dataset.

6. **MLI**: View a list of interpreted models or interpret a model.

7. **Deployments**: Deploy the MOJO and Python scoring pipelines for you to test or to integrate into a final product. You can also deploy locally or in the cloud.

8. **Resources**: The Resources dropdown menu provides you with links to view System Information, the Driverless AI User Guide and Help. From this dropdown menu, you can also download the Python Client, R Client, and the MOJO2 runtime, MOJO2 Py runtime, and MOJO2 R runtime.

9. **Messages[ ]**: View news and upcoming Driverless AI events.

10. **Logout H2OAI**: Logs you out of your current session.

11. **<**: Go back to the previous page.

12. **H2OAI**: Takes you back to the H2OAI **Datasets** Page.

13. **Driverless AI 1.X.X**: Version of Driverless AI 

14. **Add a Dataset(or Drag and Drop)**: Upload or add a dataset.


### Deeper Dive and Resources

-  [Join the H2O community on Slack to Ask Questions](https://h2oai-community.slack.com/). Post your questions, discuss use cases, give feedback, stay informed about the latest H2O.ai updates, and more.

- Learn more are about H2O Driverless through the [H2O documentation](http://docs.h2o.ai/driverless-ai/latest-stable/docs/booklets/DriverlessAIBooklet.pdf).

- [Explore H2O Product Documentation](http://docs.h2o.ai/)

- [Learn more H2O Driverless by reviewing the FAQs](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/faq.html) 


## Tarea 2: Conceptos de Machine Learning Automático(Aprendizaje de maquina)

###  Inteligencia Artificial y Machine Learning

Los conceptos que se encuentran en esta sección están destinados a proporcionar una vista general de alto nivel del Machine Learning(Aprendizaje de maquina). Al final de esta sección, podrás encontrar ligas(links) a recursos que ofrecen una explicación más profunda de los conceptos cubiertos aquí.

 Machine Learning es un sub-conjunto de Inteligencia Artificial donde el enfoque esta en crear maquinas que puedan simular la inteligencia humana. Una distinción crítica entre Intelifencia Artificial y Machine Learning es que los modelos de Machine Learning "aprenden" de los datos a los que los modelos son expuestos. Arthur Samuel, un pionero del Machine Learning en 1959, definió el Machine Learning como un "campo del estudio que le da a las computadoras la habilidad de aprender sin ser explicitamente programadas" [1]. Un algoritmo de Machine Learning se entrena con un conjunto de datos para hacer predicciones. Estas predicciones son, a veces, utilizadas para optimizar un sistema o asistir con la toma de decisiones.

### Entrenando el Machine Learning

Avances en la tecnología han facilitado la recopilación y disponibilidad de los datos. Los tipos de datos disponibles determinarán el tipo de entrenamiento al que el modelo de Machine Learning puede someterse. Hay dos tipos de entrenamiento de Machine Learning, Aprendizaje supervisado y no-supervisado. Aprendizaje supervisado es cuando el conjunto de datos contiene la salida que estás tratando de predecir. Para esos casos donde la variable de predicción no esta presente, se le llama aprendizaje no-supervisado. Ambos tipos de entrenamiento definen la relación entre variables de entrada y de salida.

En el Machine Learning, las variables de entrada son llamadas **características(features)** y las variables de salida **etiquetas(labels)**. Las etiquetas, en este caso, son las que intentamos predecir. El objetivo es tomar las entradas/características y usarlas para llegar a predicciones sobre datos nunca antes vistos. En regresión lineal, las características son las variables x, y las etiquetas son las variables y. 

Un modelo de Machine Learning define la relación entre características y etiquetas. Cuando los modelos son entrenados, puedes entrenar el modelo alimentándolo con ejemplos. Los ejemplos son una instancia particular de datos. Puedes tener dos tipos de ejemplos: etiquetados y no-etiquetados. Los ejemplos etiquetados son esos donde se conoce el valor de las variables x, y (características, etiquetas). Los ejemplos no-etiquetados son esos donde conocemos el valor de la variable x, pero no sabemos que valor tiene la variable y(características,?)[1]. Tu conjunto de datos son como un ejemplo; las columnas que se usarán para el entrenamiento son las características; las filas son las instancias de esas características. Las columnas que quieres predecir son las etiquetas.

El aprendizaje supervisado toma los ejemplos etiquetados y permite a un modelo que esta siendo entrenado aprender la relación entre características y etiquetas. El modelo entrenado es entonces probado con datos no-etiquetados, y eso permite predecir el valor de y(etiqueta) para los datos no-etiquetados. Probar un modelo entrenado con datos no-etiquetados se le llama entrenamiento no supervisado [1]. Note que H20 Driverless AI crea modelos con ejemplos etiquetados.

### Preparación de datos 

Un modelo de Machine Learning es tan bueno como los datos que se usen para entrenarlo. Si usas datos basura para entrenar tu modelo, obtendrás un modelo basura. Dicho esto, antes de cargar un conjunto de datos dentro de la herramienta que te ayudará con la construcción de tu modelo de Machine Learning como Driverless AI, asegúrate de que el conjunto de datos ha sido limpiado y preparado para el entrenamiento. Al proceso de transformación de datos en bruto en otro formato, el cual es más apropiado y valioso para el análisis, se le llama disputa de datos. 

La disputa de datos, que puede incluir extracciones, análisis, unión, estandarización, aumento, limpieza, consolidación, filtrado es altamente recomendado terminarlo antes de cargar el conjunto de datos a Driverless AI. La preparación de datos incluye el cojunto de datos en un correcto formato para lo que se intenta hacer. Los duplicados se han eliminado. Los datos perdidos se arreglan o se eliminan, y finalmente, los valores categoriales se han transformado o codificado a un tipo númerico. Finalmente, las transformaciones apropiadas en el conjunto de datos se han realizado, como el escalamiento, la descomposición y agregación, también conocido como ingeniería de características[2]. Herramientas como [Python datatable](https://datatable.readthedocs.io/en/latest/?badge=latest), [Pandas](https://pandas.pydata.org/) y [R](https://www.r-project.org/) son buenas para la disputa de datos.

Driverless AI puede hacer algunas disputas de datos. La disputa de datos se puede hacer a través de [data recipe](https://www.r-project.org/), de [JDBC connector](http://docs.h2o.ai/driverless-ai/1-8-lts/docs/userguide/connectors-nd/jdbc.html?highlight=jdbc) o a través de [live code](http://docs.h2o.ai/driverless-ai/1-8-lts/docs/userguide/datasets-describing.html?highlight=live%20code#modify-by-recipe) el cual creará un nuevo conjunto de datos modificando el existente. 

 
### Transformación de datos/Ingeniería de características

La transformación de datos o ingeniería de características es el proceso de crear nuevas características a partir de las existentes. Algunas transformacines incluyen observar todas las características e identificar cuales características pueden ser combinadas para hacer nuevas que serán más útiles para el rendimiento del modelo. Para las características categóricas, la recomendación es que las clases que tengan pocas observaciones sean agrupadas para reducir la probabilidad de que el modelo se sobreajuste(*overfitting*). Adicionalmente, variables ficticias son introducidas a las características categóricas para facilitar el Machine Learning ya que muchos algoritmos no pueden manejar características categóricas directamente. Por último pero no menos importante, eliminar características que no son usadas o son redundantes [3]. Estas son solo algunas sugerencias al acercarse a la ingeniería de características. Ingeniería de características consume mucho tiempo debido a que su naturaleza es repetitiva; también puede ser costoso. El siguiente paso en la creación de un modelo es seleccionar un algoritmo.

### Selección de algoritmo

“Los algoritmos del Machine Learning se describen como el aprendizaje de una función objetivo (f) que asigna mejor las variables de entrada (x) a una variable de salida (y): Y= f(x)”[4]. En aprendizaje supervisado, hay muchos algoritmos que seleccionar para el entrenamiento. El tipo de algoritmo(s) dependerá del tamaño de tu conjunto de datos, la estructura, y el tipo de problema que estas tratando de resolver. A través de prueba y error, se pueden encontrar los mejores algoritmos de rendimiento para tu conjunto de datos. Algunos de esos algoritmos incluyen regresión lineal, clasificación, árboles de regresión, bosques al azar, bayas ingenuas, aumentar, por nombrar algunos[5]. 

### Modelo de entrenamiento

**Conjunto de datos(datasets)** 

Una buena práctica cuando entrenamos un modelo de Machine Learning(Aprendizaje de maquina) es dividir tu conjunto de datos en sub-conjuntos: Conjuntos de entrenamiento, validación, y prueba. Una buena proporción para todo el conjunto de datos es 70-15-15, 70% de todo el conjunto de datos para el entrenamiento, 15% para la validación, y el 15% restante para la prueba. El **conjunto de entrenamiento** son los datos que se usarán para entrenar el modelo, y necesita ser suficientemente grande para obtener resultados. El **conjunto de validación** son los datos que se retuvieron del entrenamiento y se usarán para evaluar y ajustar los hiperpárametros del modelo entrenado y, por lo tanto, ajustar el rendimiento. Finalmente, El **conjunto de prueba** son datos que también se retuvieron y se usarán para confirmar los resultados del modelo final[1].

![datasets-split-ratio-diagram](assets/datasets-split-ratio-diagram.jpg)

Otra parte del entrenamiento de modelos es ajustar y adaptar los modelos. Para el ajuste y la adaptación, los hiperpárametros necesitan ser adaptados, la validación necesita llevarse a cabo usando solo los datos del entrenamiento. Varios hiperpárametros necesitarán ser probados. Adicionalmente, un ciclo de validación cruzada (validación) se establecerá para calcular los puntajes de validación para cada conjunto de hiperpárametros por cada algoritmo. Basados en los puntajes de validación cruzada y los valores de los hiperpárametros, puedes seleccionar el modelo para cada algoritmo que se adaptó con los datos del entrenamiento y probarlo usando el conjunto de prueba. El rendimiento de tu modelo de regresión puede ser evaluado por las métrica de rendimiento como son el Error Cuadrático Medio (MSE por sus siglas en inglés), la curva ROC, la Prec-Recall, LIFT, y ganancia, por mencionar algunos.

### ¿Cuáles son los desafíos al desarrollar un modelo de IA?

Uno de los desafíos importantes de cara a desarrollar un solo modelo listo para la producción es que puede llevar semanas o incluso meses construirlo. Desarrollar un modelo implica la Ingeniería de características, construcción del modelo, y la implementación del modelo. Todas las tareas son muy repetitivas, consume tiempo, requiere un conocimiento avanzado de generación de características, algoritmos, párametros, y la implementación del modelo. Finalmente, necesita haber un profundo conocimiento y confianza en como el modelo se generó para explicar y justificar cómo el modelo tomó sus decisiones.


### ¿Qué es el Machine Learning automatizado, y por qué es tan importante?

AutoML o Machine Learning Automatizado es el proceso de automatización para la selección de algoritmos, generación de características, ajuste de hiperpárametros, modelado iterativo, y la evaluación del modelo. Herramientas de AutoML como son H2O Driverless AI hace más fácil entrenar y evaluar los modelos de Machine Learning. La automatización de las tareas repetitivas del desarrollo de Machine Learning permite a las personas en la industria enfocarse en los datos y los problemas de negocios que están tratando resolver. 

### Referencias Electrónicas
[1] [Google’s Machine Learning Crash Course](https://developers.google.com/machine-learning/crash-course/training-and-test-sets/splitting-data)

[2] [About Train, Validation and Test Sets in Machine Learning](https://towardsdatascience.com/train-validation-and-test-sets-72cb40cba9e7)

[3] [Data Science Primer - Data Cleaning](https://elitedatascience.com/data-cleaning)

[4] [Feature Engineering](https://elitedatascience.com/feature-engineering) 

[5] [Towards Data Science- Supervised vs Unsupervised Learning](https://towardsdatascience.com/supervised-vs-unsupervised-learning-14f68e32ea8d) 

[6] [Selecting the best Machine Learning Algorithm for your regression problem](https://towardsdatascience.com/selecting-the-best-machine-learning-algorithm-for-your-regression-problem-20c330bad4ef)

### Exploración más profunda y recursos

- [Explore the replays from H2O World around the world](
https://www.h2o.ai/h2oworldnewyork/) 
- [Explore the webinar replays](
https://www.brighttalk.com/search/?q=driverless+ai) 
- [Explore the various H2O Driverless AI playlists on YouTube](https://www.youtube.com/user/0xdata/playlists) 


## Task 3: Load Data

1\. Navigate back to the H2O Driverless AI  **Datasets** page.

### About the Dataset

The dataset used for this experiment is a version of the Titanic Kaggle dataset. This dataset contains the list of estimated passengers aboard the RMS Titanic.

The RMS Titanic was a British commercial passenger liner that sank after colliding with an iceberg in the North Atlantic Ocean on April 15, 1912. More than 1,500 people lost their lives from an estimated 2,224 passengers and crew members while on their way to New York City from Southampton. 

This tragedy shocked the international community and led to better safety regulations for ships. The lack of lifeboats, amongst other things, was one of the factors that resulted in a significant loss of life. Although there was some element of luck involved in surviving the sinking, some groups of people were more likely to survive than others.

![rms-titanic](assets/rms-titanic.jpeg)

[RMS Titanic-Wikipedia](https://en.wikipedia.org/wiki/RMS_Titanic#/media/File:RMS_Titanic_3.jpg)

**Titanic dataset**:

1309 rows, one row per passenger, and 16 columns representing attributes of each passenger:

|Attribute|Definition|Key|
|---|---|---|
|passenger Id|Id randomly generated| - |
|pclass|Passenger Class| 1= 1st, 2 =2nd, 3=3rd|
|survived|Survival| 0=No, 1=Yes|
|name_with_salutations|Passenger name| - |
|name_without_salutations|Passenger name without salutations| - |
|sex|Sex|Female, Male|
|age|Age in years| - |
|sibsp|Number of siblings/Spouse aboard| - |
|parch|Number of Parents/Children aboard| - |
|ticket|Ticket number| - |
|fare|Passenger fare| - |
|cabin|Cabin number| - |
|embarked|Port of Embarkment|C = Cherbourg, Q = Queenstown, S = Southampton|
|boat|Boat number| - |
|body|Body number| - |
|home.des|Home Destination| - |


### Add the Data 

1\. Click on **Add a Dataset(or Drag and Drop)**  

2\. Select **FILE SYSTEM**

![add-dataset-file-system](assets/add-dataset-file-system.jpg)

3\. Enter the following */data/TestDrive/titanic.csv* into the search bar. Select *titanic.csv* then **Click to Import Selection**. 

![select-titanic-dataset](assets/select-titanic-dataset.jpg)


4\. If the file loaded successfully, then you should see an  image similar to the one below:

![titanic-set-overview](assets/titanic-set-overview.jpg)

*Things to Note:*

1. You can view:

  - Dataset filename
  - File size
  - Number of rows/columns 
  - File status

2. Option to go back to the previous page  

### Deeper Dive and Resources

- [Learn More About the Type of Dataset File formats that Can be Uploaded](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/datasets.html#adding-datasets) 

- For more datasets, check out [Kaggle Datasets](https://www.kaggle.com/datasets)

## Task 4: Explore Data Details and AutoViz

### Details

We are now going to explore the Titanic dataset that we just loaded. 

1\. Continuing on the **Dataset Overview page**, click on the titanic.csv dataset. The following options will appear:

![titanic-set-actions](assets/titanic-set-actions.jpg)

 - Details - View a summary of the dataset or preview the dataset
 - Visualize - Visualize the dataset with available graphs
 - Split - Split the dataset
 - Predict - Run an experiment using Driverless AI
 - Rename - Rename the dataset
 - Download - Download the dataset
 - Delete - Delete the dataset 

**Note**: A dataset can only be deleted if it's not being used in an experiment. Otherwise, you must delete the experiment first, and then the dataset can be deleted.

2\. Next, we are going to confirm that the dataset loaded correctly and that it has the correct number of rows and columns by clicking on **Details**.

3\. Click on **Details**.  **Details** will take you to the **Dataset Details Page**
 
 ![titanic-set-details-page](assets/titanic-set-details-page.jpg)

*Things to Note:*

1. The **Dataset Details Page** provides a summary of the dataset. This summary lists each column that is included in the dataset along with:

    **Logical type (can be changed)**

    ![logical-type-options](assets/logical-type-options.jpg)

    **Format for Date and Datetime columns(can be changed)**

    ![dataset-details-format-option](assets/dataset-details-format-option.jpg)

    - Storage type
    - Count
    - Number of missing values
    - Mean
    - Minimum
    - Maximum
    - Standard deviation
    - Frequency
    - Number of unique values
    - View the first 20 rows of a column

    ![datasets-details-first-20-rows](assets/datasets-details-first-20-rows.jpg)

    **Note**: Driverless AI recognizes the following column types: integer, string, real, boolean, and time. Date columns are given a string "str" type.

2. You can view information for a specific column by entering the name of the column in the field above the graph.

3. **Modify by Recipe** allows you to create a new dataset by modifying an existing dataset with custom recipes.

4. **Dataset Rows** allows you to preview the dataset

5. Option to exit and return to the H2O **Datasets** page

4\. Select  **Dataset Rows**    

![titanic-set-rows-page](assets/titanic-set-rows-page.jpg)

*Things to Note:*
 1. Preview the dataset 
 2. View the remaining rows
 3. **Modify by Recipe** - Modify the dataset through a custom recipe
 3. Return to the **Dataset Overview** 
 4. Option to Exit and return to the H2O **Datasets** page

5\. Exit and return to **Datasets Overview** page.

### Split the Dataset

From the Titanic.csv dataset, we are going to create two datasets, training and test. 75% of the data will be used for training the model, and 25% to test the trained model.

1\. Click on the titanic.csv file and select **Split** 

![titanic-set-split-1](assets/titanic-set-split-1.jpg)

2\. Split the data into two sets: titanic_train and titanic_test, then save the changes. Use the image below as a guide: 

![titanic-set-split-2](assets/titanic-set-split-2.jpg)

*Things to Note:*

1. For OUTPUT NAME 1: enter ```titanic_train``` (this will serve as the training set)
2. For OUTPUT NAME 2: enter ```titanic_test``` (this will serve as the test set)
3. You can change the Random Seed; this will generate the same split every time
4. Change the split value to .75 by adjusting the slider to 75% or entering .75 in the section that says *Train/Valid Split Ratio*
5. Save the changes you made 

The ratio of .75 was selected for this particular dataset to not generalize the model given the total size of the set.

**The training set** contains 981 rows, each row representing a passenger, and 16 columns representing the attributes of each passenger.

**The Test set** contains 328 rows, each row representing a passenger, and 16 attribute columns representing attributes of each passenger. 

Verify that the three Titanic datasets, titanic_test, titanic_train and titanic.csv are there:

![three-datasets](assets/three-datasets.jpg)

### Autoviz

Now that the titanic.csv dataset has been split, we will use the **titanic_train** set for the remaining of the tutorial.

There are two ways to visualize the training set:

![titanic-train-visualize](assets/titanic-train-visualize.jpg)

**Method 1** : Clicking on the **titanic_train** file, select **Visualize**, then click on the visualization file generated.



**Method 2**: Clicking on  **Autoviz** located at the top of the UI page, where you will be asked for the dataset you want to visualize.

1\. Pick a method to visualize the **titanic_train** dataset. A similar image should appear:

![train-set-visualization-ready](assets/train-set-visualization-ready.jpg)

Click on the **titanic_train** visualization, and the following screen will appear.

![train-set-visualizations](assets/train-set-visualizations.jpg)

Is it possible to visualize how variables on the training set are correlated? Can we determine what other variables are strongly correlated to a passenger's survival? The answer to those questions is yes! One of the graphs that allow us to visualize the correlations between variables is the **Correlation Graph**.

Let's explore the correlation between the 'survived' variable and other variables in the dataset.

2\. Select the **Correlation Graph** and then click on **Help** located at the lower-left corner of the graph. 

3\. Take a minute to read about how the correlation graph was constructed.  Learn more about how variables are color-coded to show their correlations. 

4\. Take the 'survived' variable and drag it slightly to have a better look at the other variables Driverless AI found it is correlated to. 

What variables are strongly correlated with the 'survived' variable?

![train-set-correlation-graph](assets/train-set-correlation-graph.jpg)

*Things to Note:*

 - The **Help** button explains the **Correlation Graph**. This feature is available for all graphs.
 - **Download** allows for a full-scale image of the graph to be downloaded

5\. Exit out of the **Correlation Graph** view by clicking on the **X** at the top-right corner of the graph.

6\. After you are done exploring the other graphs, go back to the **datasets page**.

Driverless AI  shows the graphs that are "relevant" aspects of the data. The following are the type of graphs available:

- Correlated Scatterplots
- Spikey Histograms
- Skewed Histograms
- Varying Boxplots
- Heteroscedastic Boxplots
- Biplots
- Outliers
- Correlation Graph
- Parallel Coordinates Plot
- Radar Plot
- Data Heatmap
- Missing Values Heatmap
- Gaps Histogram


### Deeper Dive and Resources

- [Learn more about Automatic Visualization from the Driverless docs](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/datasets.html#visualizing-datasets)

- [Learn more about Automatic Visualization from the architect Leland Wilkinson, Chief Scientist, H2O.ai from session at H2O World 2017 Youtube Video](https://www.youtube.com/watch?v=bas3-Ue2qxc)

- [Automatic Visualization SlideShare](https://www.slideshare.net/0xdata/automatic-visualization)

## Task 5: Launch First Experiment

We are going to launch our first experiment. An experiment means that we are going to generate a prediction using a dataset of our choice.

1\. Return to  the **Dataset Overview page**

2\. Click on the **titanic_train** dataset then select **Predict**

![titanic-train-predict](assets/titanic-train-predict.jpg)

If this is your first time launching an experiment, the following prompt will appear, asking if you want to take a tour.  

![driverless-tour](assets/driverless-tour.jpg)

If you would like to take a quick tour of the **Experiments** page, select **YES**, the quick tour will cover the following items:

- Select the training dataset 
- Select the target column that you want Driverless AI to predict from all columns
- Select if it is a Time Series problem or not [Time Series ON or OFF]

3\. Select **Not Now** to come back and take the tour another time.

4\. The following  **Experiment** page will appear:

![train-set-experiment-page](assets/train-set-experiment-page.jpg)

*Things to Note:*

0. Assistant - Interactive tour for first-time users. 
Click on  **assistant** to enable it. Yellow circles appear around selected sections of the experiment setup page. You can hover any of them to get more info on each section. 

Note: To disable **assistant**, click on assistant again.

![titanic-train-assist-sample](assets/titanic-train-assist-sample.jpg)
 
 
1. **Display Name** - Type the name for your experiment `Titanic Classification Tutorial.`
2. **Dataset** - the name of the dataset being used to create an experiment
3. **Rows** - total number of rows 
4. **Columns** - total number of columns 
5. **Dropped Columns** - Drop column(s) from your dataset that you don't want to use in the experiment
6. **Validation Dataset** - Select the dataset you want to validate. This set will be used to validate parameters like models, features, etc.
7. **Test Dataset** - The dataset that will be used to test the model generated from the training dataset. It's not used during training of the model, and results are available at the end of the experiment.
8. **Target column** -  What do you want to predict? 
9. **Fold column** - The fold column is used to create the training and validation datasets so that all rows with the same Fold value will be in the same dataset
10. **Weight column** - Column that indicates the observation weight (a.k.a. sample or row weight), if applicable.  
11. **Time Column**(OFF by default) - Provides a time order(timestamps for observations). Used when data has a high dependency on time (such as seasonality or trend), and you want to treat this problem as a time series problem. 

Continuing with our experiment:

5\. Click **Dropped Columns**, drop the the following columns: Passenger_Id, name_with_salutations, name_without_salutations, boat, body and home.dest. Then select **Done**. 

![train-set-drop-columns](assets/train-set-drop-columns.jpg)

These attributes (columns) were removed to create a cleaner dataset. Attributes such as boat and body are excluded because they are clear indicators that a passenger survived and can lead to data leakage. For our experiment, the survived column will suffice to create a model. 

A clean dataset is essential for the creation of a good predictive model. The process of data cleansing needs to be done with all datasets to rid the set of any unwanted observations, structural errors, unwanted outliers, or missing data. 

6\. Select **Test Dataset** and then click on **titanic_test**

![add-test-set](assets/add-test-set.jpg)

7\. Now select the **Target Column**. In our case, the column will be 'survived.'

![train-set-drop-name-column](assets/train-set-drop-name-column.jpg)

The survived attribute was selected because, as an insurance company, we want to know what other attributes can contribute to the survival of passengers aboard a ship and incorporate that into our insurance rates.

8\. Your experiment page should look similar to the one below; these are the system suggestions:

![experiment-settings](assets/experiment-settings.jpg)

*Things to Note:*

1. **Training Settings** - Describes the Accuracy, Time, and Interpretability of your specific experiment.  The knobs on the experiment settings are adjustable as values change the meaning of the settings on the left-bottom page change.
    - **Accuracy** - (Relative accuracy) higher values, should lead to higher confidence in model performance (accuracy).
    - **Time** - Relative time for completing the experiment. Higher values will take longer for the experiment to complete.
    - **Interpretability** -  The degree to which a human can understand the cause of the decision.  
2. **Expert Settings** - Available expert settings to customize your experiment. 
3. **Scorer** - Driverless AI selects the best scorer based on your dataset. Other scorers can be manually selected.
4. **Classification** - Classification or Regression button. Driverless AI automatically determines the problem type based on the response column. Though not recommended, you can override this setting by clicking this button. 
5. **Reproducible** - This button allows you to build an experiment with a random seed and get reproducible results. If this is disabled (default), the results will vary between runs.
6. **GPUs Enabled** - Specify whether to enable GPUs. (Note that this option is ignored on CPU-only systems)
7. **Launch Experiment** - Launches the experiment


9\. Update the following experiment settings so that they match the image below, then select **Launch Experiment**.

- Accuracy: 4
- Time: 2
- Interpretability: 6
- Scorer: AUC
- Reproducible:  Enabled (Click on Reproducible)

![update-experiment-settings](assets/update-experiment-settings.jpg)

**Note**: To Launch an Experiment: The dataset and the target column are the minimum elements required to launch an experiment.

10\. The **Experiment** page will look similar to the one below after 45% complete:

![experiment-running-45](assets/experiment-running-45.jpg)

*Things to Note:*
1. **Experiment Name** - Name of your experiment. If you do not assign a name to it, a random name will be generated. The name can be changed at any time.
2. **Experiment Setup** - Summary of experiment setup and dataset details.
3. **Running Status Display** - Status of parameter tuning followed by feature engineering and scoring pipeline. Experiments can be stopped by clicking the ```Finish``` button.
4. Overview of training settings (unable to adjust the while experiment is running): **Training Settings**, **Experiment Settings**, **Scorer**, **Classification**, **Reproducible** and **GPU Enabled**. 
5. **CPU/Memory** information including **Notifications**, **Logs**, and **Trace** info. (Note that Trace is used for development/debugging and to show what the system is doing at that moment.) **Scorers** or model scorers allow you to view the detailed information about model scores after an experiment is complete. **Scorers** includes model and feature tuning leaderboard, single final model cross-validation fold scores, and final ensemble scores.
6. **Iteration Data** and **Variable Importance** - Iteration Data is the internal validation for each cross-validation fold with the specified scorer value. You can hover over any of the iteration points in the Iteration Data graph, and the see the updated variable importance for that iteration on the **Variable Importance**
7. **Classification Problem Graphs** - Toggle between a ROC curve, Precision-Recall graph, Lift chart, Gains chart, and GPU Usage information (if GPUs are available). For regression problems, the lower right section includes a toggle between a Residuals chart, an Actual vs. Predicted chart, and GPU Usage information (if GPUs are available). 
                                                            
Once the experiment is complete, an **Experiment Summary** will appear:

![experiment-summary](assets/experiment-summary.jpg)

*Things to Note:*
1. Status Complete Options
    - Deploy (Local and Cloud)
    - Interpret This Model 
    - Diagnose Model On New Dataset 
    - Score on Another Dataset
    - Transform Another Dataset
    - Download Predictions
        - Training Predictions
        - Validation Set Predictions(available if a validation set was provided)
        - Test Set Predictions
    - Download Python Scoring Pipeline - A standalone Python Scoring pipeline that downloads a package containing an exported model and Python 3.6 source code examples for productionizing models built using H2O Driverless AI. 
    - Download MOJO Scoring Pipeline - A standalone scoring pipeline that converts experiments to MOJO's, which can be scored in realtime. It is available as either Java runtime or a C++ runtime(with Python and R wrappers).
    - Visualize Scoring Pipeline(Experimental): A visualization of the scoring pipeline is available for each completed experiment.

    ![visualize-scoring-pipeline-experimental](assets/visualize-scoring-pipeline-experimental.jpg)

    - Download Experiment Summary - A zip file providing textual explanations of the graphical representations that are shown in the Driverless AI UI.
        - Experiment logs (regular and anonymized)
        - A summary of the experiment
        - The experiment features along with their relative importance
        - Ensemble information
        - An experiment preview
        - Word version of an auto-generated report for the experiment
        - Target transformations tuning leaderboard
        - A tuning leaderboard
 
    - Download Autoreport - This report provides insight into the training data and any detected shifts in distribution, the validation schema selected, model parameter tuning, feature evolution, and the final set of features chosen during the experiment.

2. Iteration Data - Validation/Variable Importance - Summary of top 20 - Feature Engineered variables

3. Experiment Graphs and Summary - This section describes the dashboard graphs that display for running and completed experiments. These graphs are interactive. Hover over a point on the graph for more details about the point.

### Deeper Dive and Resources

- [Learn more about running Experiments from H2O Driverless AI docs](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/running-experiment.html#)

- [Explore Documentation on Completed Experiments](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/experiment-completed.html)

- [Explore Documentation on Visualizing the Scoring Pipeline](http://docs.h2o.ai/driverless-ai/1-8-lts/docs/userguide/scoring_pipeline_visualize.html?highlight=visualize%20scoring%20pipeline)

- [Explore Documentation on Experiment Summary](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/experiment-summary.html) 

- [Review the Driverless AI Booklet to learn more about running experiments](http://docs.h2o.ai/driverless-ai/latest-stable/docs/booklets/DriverlessAIBooklet.pdf) 


## Task 6: Explore Feature Engineering

Driverless AI performs feature Engineering on the dataset to determine the optimal representation of the data. Various stages of the features appear throughout the iteration of the data. These can be viewed by hovering over points on the Iteration Data - Validation Graph and seeing the updates on the **Variable Importance** section.

![feature-engineering-1](assets/feature-engineering-1.jpg)

Transformations in Driverless AI are applied to columns in the data. The transformers create engineered features in experiments. There are many types of transformers, below are just some of the transformers found in our dataset:

1\. Look at some of the variables in **Variable of Importance**. Note that some of the variables start with ```CVTE``` followed by a column from the dataset. Some other variables might also begin with ```_NumToCatTE```, ```Freq``` or ```_WoE``` depending on the experiment you run. These are the new, high-value features for our training dataset.

These transformations are created with the following transformers:

- Cross Validation Target Encoding Transformer: ```_CVTargetEncode```
- Weight of Evidence : ```WoE```
- Frequent Transformer: ```Freq```  
- Numeric to Categorical Target Encoding Transformer = ```_NumToCatTE```

You can also hover over any of the variables under variable importance to get a simple explanation of the transformer used as seen in the image below:

![variable-importance-hover-for-transformer](assets/variable-importance-hover-for-transformer.jpg)

The complete list of features used in the final model is available in the Experiment Summary artifacts. The Experiment Summary also provides a list of the original features and their estimated feature importance. 

### Deeper Dive and Resources

- [Learn more about Driverless AI Transformations](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/transformations.html) 

- [Feature Engineering for Machine Learning by Dmitry Larko](https://www.youtube.com/playlist?list=PLrsf4weWJKynQBvh0i-YxDDVqCcIrF28o) 

- [H2O World London 2018 Feature Engineering session replay](https://www.youtube.com/watch?v=d6UMEmeXB6o ) and [slides  by Dmitry](https://www.slideshare.net/0xdata/feature-engineering-in-h2o-driverless-ai-dmitry-larko-h2o-ai-world-london-2018 ) 

## Task 7: Explore Experiment Results

Let’s explore the results of this classification experiment. You can find the results on the **Experiment Summary** at the left-bottom of **Experiment** page. The resulting plots are insights from the training and validation data resulting from the classification problem. Each plot will be given a brief overview. 

If you are interested in learning more about each plot and the metrics derived from those plots covered in this section, then check out our next tutorial [Machine Learning Experiment Scoring and Analysis Tutorial - Financial Focus](https://h2oai.github.io/tutorials/machine-learning-experiment-scoring-and-analysis-tutorial-financial-focus/#0).

![experiment-summary-expanded](assets/experiment-summary-expanded.jpg)

1\. Summary

Once the experiment is done, a summary is generated at the bottom-right corner of the **Experiment** page.

The summary includes:

- **Experiment**: experiment name,
  - Version: the version of Driverless AI and the date it was launched
  - Settings: selected experiment settings, seed, and amount of GPU’s enabled
  - Train data: name of the training set, number of rows and columns
  - Validation data: name of  the validation set, number of rows and columns
  - Test data: name of the test set, number of rows and columns
  - Target column: name of the target column (the type of data and % target class)

- **System Specs**: machine specs including RAM, number of CPU cores and GPU’s
  - Max memory usage  

- **Recipe**: 
  - Validation scheme: type of sampling, number of internal holdouts
  - Feature Engineering: number of features scored and the final selection

- **Timing**
  - Data preparation 
  - Shift/Leakage detection
  - Model and feature tuning: total time for model and feature training and  number of models trained 
  - Feature evolution: total time for feature evolution and number of models trained 
  - Final pipeline training: total time for final pipeline training and the total models trained 
  - Python / MOJO scorer building 
- Validation Score: Log loss score +/- machine epsilon for the baseline
- Validation Score: Log loss score +/- machine epsilon for the final pipeline
- Test Score: Log loss score +/- machine epsilon score for the final pipeline 

Most of the information in the Experiment Summary tab, along with additional detail, can be found in the Experiment Summary Report (Yellow Button “Download Experiment Summary”).

1. Find the number of features that were scored for your model and the total features that were selected. 

2. Take a look at the validation Score for the final pipeline and compare that value to the test score. Based on those scores, would you consider this model a good or bad model? 

2\. ROC - Receiver Operating Characteristics

This type of graph is called a Receiver Operating Characteristic curve (or ROC curve.) It is a plot of the true positive rate against the false-positive rate for the different possible cutpoints of a diagnostic test.

An ROC curve is a useful tool because it only focuses on how well the model was able to distinguish between classes. “AUC’s can help represent the probability that the classifier will rank a randomly selected positive observation higher than a randomly selected negative observation”[1].  However, for models where the prediction happens rarely, a high AUC could provide a false sense that the model is correctly predicting the results.  This is where the notion of precision and recall become essential.

The ROC curve below shows Receiver-Operator Characteristics curve stats on validation data along with the best Accuracy, FCC, and F1 values[2].

![experiment-results-roc-graph](assets/experiment-results-roc-graph.jpg)

This ROC gives an Area Under the Curve or AUC of .8530. The AUC tells us that the model is able to classify the survivors 85.30% of the time correctly.  

Learn more about the ROC Curve on [Machine Learning Experiment Scoring and Analysis Tutorial - Financial Focus: ROC](https://h2oai.github.io/tutorials/machine-learning-experiment-scoring-and-analysis-tutorial-financial-focus/#7).

3\. Prec-Recall - Precision-Recall graph

Prec-Recall is a complementary tool to ROC curves, especially when the dataset has a significant skew. The Prec-Recall curve plots the precision or positive predictive value (y-axis) versus sensitivity or true positive rate (x-axis) for every possible classification threshold. At a high level, we can think of precision as a measure of exactness or quality of the results while recall as a measure of completeness or quantity of the results obtained by the model. Prec-Recall measures the relevance of the results obtained by the model.

The Prec-Recall plot below shows the Precision-Recall curve on validation data along with the best Accuracy, FCC, and F1 values. The area under this curve is called AUCPR.

![experiment-results-prec-recall-graph](assets/experiment-results-prec-recall-graph.jpg)

Similarly to the ROC curve, when we take a look at the area under the curve of the Prec-Recall Curve of AUCPR we get a value of .7960. This tells us that the model brings forth relevant results or those cases of the passengers that survived 79.60% of the time.

Learn more about the Prec-Curve Curve on [Machine Learning Experiment Scoring and Analysis Tutorial - Financial Focus: Prec-Recall](https://h2oai.github.io/tutorials/machine-learning-experiment-scoring-and-analysis-tutorial-financial-focus/#8).

4\. Cumulative Lift Chart 

Lift can help us answer the question of how much better one can expect to do with the predictive model compared to a random model(or no model). Lift is a measure of the effectiveness of a predictive model calculated as the ratio between the results obtained with a model and with a random model(or no model). In other words, the ratio of gain% to the random expectation % at a given quantile. The random expectation of the xth quantile is x%[4].

The Cumulative Lift chart shows lift stats on validation data. For example, “How many times more observations of the positive target class are in the top predicted 1%, 2%, 10%, etc. (cumulative) compared to selecting observations randomly?” By definition, the Lift at 100% is 1.0.

![experiment-results-lift-graph](assets/experiment-results-lift-graph.jpg)

Learn more about the Cumulative Lift Chart on [Machine Learning Experiment Scoring and Analysis Tutorial - Financial Focus: Cumulative Lift](https://h2oai.github.io/tutorials/machine-learning-experiment-scoring-and-analysis-tutorial-financial-focus/#10).

5\. Cumulative Gains Chart

Gain and Lift charts measure the effectiveness of a classification model by looking at the ratio between the results obtained with a trained model versus a random model(or no model)[3]. The Gain and Lift charts help us evaluate the performance of the classifier as well as answer questions such as what percentage of the dataset captured has a positive response as a function of the selected percentage of a sample. Additionally, we can explore how much better we can expect to do with a model compared to a random model(or no model)[4].

For better visualization, the percentage of positive responses compared to a selected percentage sample, we use Cumulative Gains and Quantile. 

In the Gains Chart below, the x-axis shows the percentage of cases from the total number of cases in the test dataset, while the y-axis shows the percentage of positive outcomes or survivors in terms of quantiles.

The Cumulative Gains Chart below shows Gains stats on validation data. For example, “What fraction of all observations of the positive target class are in the top predicted 1%, 2%, 10%, etc. (cumulative)?” By definition, the Gains at 100% are 1.0.

![experiment-results-gains-graph](assets/experiment-results-gains-graph.jpg)

The Gains chart above tells us that when looking at the 20% quantile, the model can positively identify ~45% of the survivors compared to a random model(or no model) which would be able to positively identify about ~20% of the survivors at the 20% quantile.

Learn more about the Cumulative Gains Chart on [Machine Learning Experiment Scoring and Analysis Tutorial - Financial Focus: Cumulative Gains](https://h2oai.github.io/tutorials/machine-learning-experiment-scoring-and-analysis-tutorial-financial-focus/#9).

6\. K-S

Kolmogorov-Smirnov or K-S measures the performance of classification models by measuring the degree of separation between positives and negatives for validation or test data[5]. “The K-S is 100 if the scores partition the population into two separate groups in which one group contains all the positives and the other all the negatives. On the other hand, If the model cannot differentiate between positives and negatives, then it is as if the model selects cases randomly from the population. The K-S would be 0. In most classification models, the K-S will fall between 0 and 100, and that the higher the value, the better the model is at separating the positive from negative cases.”[6].

K-S or the Kolmogorov-Smirnov chart measures the degree of separation between positives and negatives for validation or test data.

Hover over a point in the chart to view the quantile percentage and Kolmogorov-Smirnov value for that point.

![experiment-results-gains-k-s](assets/experiment-results-gains-k-s.jpg)

For the K-S chart above, if we look at the top 60% of the data, the at-chance model (the dotted diagonal line) tells us that only 60% of the data was successfully separate between positives and negatives (survived and did not survived). However, with the model, it was able to do .499, or about 50% of the cases were successfully separated between positives and negatives.

Learn more about the Kolmogorov-Smirnov chart on [Machine Learning Experiment Scoring and Analysis Tutorial - Financial Focus: Kolmogorov-Smirnov chart](https://h2oai.github.io/tutorials/machine-learning-experiment-scoring-and-analysis-tutorial-financial-focus/#11).

### References
 
[1] [ROC Curves and Under the Curve (AUC) Explained](https://www.youtube.com/watch?v=OAl6eAyP-yo)

[2] [H2O Driverless AI - Experiment Graphs](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/experiment-graphs.html?highlight=roc%20curve)

[3] [Model Evaluation Classification](https://www.saedsayad.com/model_evaluation_c.htm)

[4] [Lift Analysis Data Scientist Secret Weapon](https://www.kdnuggets.com/2016/03/lift-analysis-data-scientist-secret-weapon.html)

[5] [H2O’s Kolmogorov-Smirnov](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/experiment-graphs.html?highlight=mcc)

[6] [Model Evaluation- Classification](https://www.saedsayad.com/model_evaluation_c.htm)


### Deeper Dive and Resources

- [The Best Metric to Measure Accuracy of Classification Models](https://clevertap.com/blog/the-best-metric-to-measure-accuracy-of-classification-models/)

## Task 8: MLI Report for Non-Time-Series

After the predictive model is finished, we can explore the interpretability of our model. In other words, what are the results and how did those results come to be?

Questions to consider before viewing the MLI Report:

- Which attributes from our Titanic Training Set are the most important in relation to surviving? Make a note of your top 2 attributes to compare it with the model's results

There are two ways to generate the MLI Report, selecting the **MLI** link on the upper-right corner of the UI or clicking **Interpret this Model** button on the **Experiment** page. 

**Generate the MLI report**:

1\. **On the Status: Complete** Options, select **Interpret this Model**

![interpret-this-model](assets/interpret-this-model.jpg)

2\. Once the MLI model is complete, you should see an image similar to the one below:

![finishing-up-mli](assets/finishing-up-mli.jpg)

3\. Once the **MLI Experiment is finished** a pop up comes up, go to MLI page by clicking **Yes**.

4\. The MLI Interpretability Page has the explanations to the model results in a human-readable format.  

This section describes MLI functionality and features for regular experiments. For non-time-series experiments, this page provides several visual explanations and reason codes for the trained Driverless AI  model, and it's results.  

![mli-report-page-1](assets/mli-report-page-1.jpg)
![mli-report-page-2](assets/mli-report-page-2.jpg)

*Things to Note:*
1. Summary -  Summary of MLI experiment. This page provides an overview of the interpretation, including the dataset and Driverless AI experiment (if available) that were used for the interpretation along with the feature space (original or transformed), target column, problem type, and k-Lime information.

2. Driverless AI Model: For binary classification and regression experiments, the Driverless AI Model menu provides the following plots for Driverless AI models:

    - **Feature Importance for transformed features**: This plot shows the Driverless AI feature importance. Driverless AI feature importance is a measure of the contribution of an input variable to the overall predictions of the Driverless AI model. Global feature importance is calculated by aggregating the improvement in splitting criterion caused by a single variable across all of the decision trees in the Driverless AI model.

    ![dai-model-feature-importance](assets/dai-model-feature-importance.jpg)

    - **Shapley plots for transformed features**: Shapley explanations are a technique with credible theoretical support that presents consistent global and local variable contributions. Local numeric Shapley values are calculated by tracing single rows of data through a trained tree ensemble and aggregating the contribution of each input variable as the row of data moves through the trained ensemble. For regression tasks, Shapley values sum to the prediction of the Driverless AI model. For classification problems, Shapley values sum to the prediction of the Driverless AI model before applying the link function. Global Shapley values are the average of the absolute Shapley values over every row of a dataset.

    ![dai-model-shapley](assets/dai-model-shapley.jpg)

    - **Partial Dependence/ICE Plot** :  
    
    Partial dependence is a measure of the average model prediction with respect to an input variable. Partial dependence plots display how machine-learned response functions change based on the values of an input variable of interest while considering nonlinearity and averaging out the effects of all other input variables. Partial dependence plots are well-known and described in the Elements of Statistical Learning (Hastie et al., 2001). Partial dependence plots enable increased transparency in Driverless AI models and the ability to validate and debug Driverless AI models by comparing a variable's average predictions across its domain to known standards, domain knowledge, and reasonable expectations. 
    
    Individual conditional expectation (ICE) plots, a newer and less well-known adaptation of partial dependence plots, can be used to create more localized explanations for a single individual using the same basic ideas as partial dependence plots. ICE Plots were described by Goldstein et al. (2015). ICE values are simply disaggregated partial dependence, but ICE is also a type of nonlinear sensitivity analysis in which the model predictions for a single row are measured. At the same time, a variable of interest is varied over its domain. ICE plots enable a user to determine whether the model's treatment of an individual row of data is outside one standard deviation from the average model behavior, whether the treatment of a specific row is valid in comparison to average model behavior, known standards, domain knowledge, and reasonable expectations, and how a model will behave in hypothetical situations where one variable in a selected row is varied across its domain.

    ![dai-model-partial-dependence-ice](assets/dai-model-partial-dependence-ice.jpg)

    - **Disparate Impact Analysis(NEW)**: Disparate Impact Analysis is a technique that is used to evaluate fairness. Bias can be introduced to models during the process of collecting, processing, and labeling data—as a result, it is essential to determine whether a model is harming certain users by making a significant number of biased decisions. Learn more about [Disparate Impact Analysis](http://docs.h2o.ai/driverless-ai/1-8-lts/docs/userguide/interpret-non-ts.html#disparate-impact-analysis).

    ![dai-disparate-impact-analysis-1](assets/dai-disparate-impact-analysis-1.jpg)

    ![dai-disparate-impact-analysis-2](assets/dai-disparate-impact-analysis-2.jpg)

    ![dai-disparate-impact-analysis-3](assets/dai-disparate-impact-analysis-3.jpg)

    - **Sensitivity Analysis(NEW)** : 
    
    Sensitivity Analysis (or "What if?") is a simple and powerful model debugging, explanation, fairness, and security tool. The idea behind Sensitivity Analysis is both direct and straightforward: Score your trained model on a single row, on multiple rows, or an entire dataset of potentially interesting simulated values and compare the model's new outcome to the predicted outcome on the original data.

    Sensitivity analysis investigates whether model behavior and outputs remain stable when data is intentionally perturbed, or other changes are simulated in the data. Machine learning models can make drastically differing predictions for only minor changes in input variable values. For example, when looking at predictions that determine financial decisions, SA can be used to help you understand the impact of changing the most important input variables and the impact of changing socially sensitive variables (such as Sex, Age, Race, etc.) in the model. If the model changes in reasonable and expected ways when important variable values are changed, this can enhance trust in the model. Similarly, if the model changes to sensitive variables have minimal impact on the model, then this is an indication of fairness in the model predictions.

    Learn more about [Sensitivity Analysis](http://docs.h2o.ai/driverless-ai/1-8-lts/docs/userguide/interpret-non-ts.html#sensitivity-analysis).

    ![dai-sensitivity-analysis](assets/dai-sensitivity-analysis.jpg)

    - **NLP Tokens (for text experiments only)**: This plot shows both the global and local importance values of each token in a corpus (a large and structured set of texts). The corpus is automatically generated from text features used by Driverless AI models prior to the process of tokenization

    - **NLP LOCO (for text experiments)**: This plot applies a leave-one-covariate-out (LOCO) styled approach to NLP models by removing a specific token from all text features in a record and predicting local importance without that token. The difference between the resulting score and the original score (token included) is useful when trying to determine how specific changes to text features alter the predictions made by the model.

    - [See documentation for multiclass classification and time-series experiments](http://docs.h2o.ai/driverless-ai/1-8-lts/docs/userguide/interpret-non-ts.html#summary-page)

3. Surrogate Models - For classification and regression experiments

    - **KLIME**

    ![surrogate-models-klime](assets/surrogate-models-klime.jpg)

    - **Decision Tree**

    ![surrogate-models-decision-tree](assets/surrogate-models-decision-tree.jpg)

    - **Random Forest - Feature Importance**

    ![surrogate-models-rf-feature-importance](assets/surrogate-models-rf-feature-importance.jpg)
    
    - **Random Forest - Partial Dependence**

    ![surrogate-models-rf-partial-dependence-plot](assets/surrogate-models-rf-partial-dependence-plot.jpg)

    - **Random Forest - LOCO**

    ![surrogate-models-rf-loco](assets/surrogate-models-rf-loco.jpg)

4. **Dashboard** - The Model Interpretation Page includes the following:
    - K-Lime: Global Interpretability Model Explanation Plot
    - Feature Importance: Surrogate RF Feature Importance
    - Decision Tree Surrogate model
    - Partial Dependence and Individual Conditional Expectation (ICE) plots

5. MLI Docs - Link to the "Machine Learning Interpretability with 
Driverless AI" booklet
6. Download MLI Logs 
7. Experiment - Link to return to the experiment that generated the current interpretation
8. Scoring Pipeline - Download the scoring pipeline for the current interpretation
9. Download Reason Codes - Download a CSV file of LIME or Shapley reason codes
10. Datasets - Takes you back to the Datasets page 
11. Experiments - Takes you back to the Experiments page
12. MLI - Takes you back to the MLI page 
13. Row selection - The row selection feature allows a user to search for a particular observation by row number or by an identifier column. Identifier columns cannot be specified by the user - MLI makes this choice automatically by choosing columns whose values are unique (dataset row count equals the number of unique values in a column).


### MLI Dashboard

Select the MLI **Dashboard** and explore the different types of insights and explanations regarding the model and its results. All plots are interactive.

![mli-dashboard](assets/mli-dashboard.jpg)

1\. K-Lime - Global Interpretability model explanation plot: 
This plot shows Driverless AI model and LIME model predictions in sorted order by the Driverless AI model predictions. In white, is the global linear model of Driverless AI predictions (middle green).
1. Hover over any of the points of the plot and view the LIME reason codes for that value.
2. Select a point where *Actual value* is 1 and note the reason codes for that prediction value

![dashboard-klime](assets/dashboard-klime.jpg)

Learn more about K-Lime with our [Machine Learning Interpretability Tutorial](https://h2oai.github.io/tutorials/machine-learning-interpretability-tutorial/#7).

2\. Feature Importance - 
This graph shows the essential features that drive the model behavior.
1. Which attribute/feature had the most importance?
2. Was this the same attribute that you hypothesized?
3. View the explanation of the **Variable Importance** plot by selecting **About this plot**

![dashboard-feature-importance](assets/dashboard-feature-importance.jpg)

Learn more about Feature Importance with our [Machine Learning Interpretability TUtorial](https://h2oai.github.io/tutorials/machine-learning-interpretability-tutorial/#4).

3\. Decision Tree Surrogate model
The decision Tree Surrogate model displays the model's approximate flowchart of the complex Driverless AI model's decision making.                  
Higher and more frequent features are more important. Features above or below one-another can indicate an interaction. Finally, the thickest edges are the most common decision paths through the tree that lead to a predicted numerical outcome.

1. What is the most common decision path for the Titanic Training set?

Solution:

![decision-tree-task-8-answer](assets/decision-tree-task-8-answer.jpg)

Learn more about Decision Trees with our [Machine Learning Interpretability Tutorial](https://h2oai.github.io/tutorials/machine-learning-interpretability-tutorial/#6).

4\. Partial Dependence and Individual Conditional Expectation (ICE) plot. This plot represents the model prediction for different values of the original variables. It shows the average model behavior for important original variables.

The grey bar represents the standard deviation of predictions. The yellow dot represents the average predictions.

![dashboard-partial-dependence-plot](assets/dashboard-partial-dependence-plot.jpg)

1. Explore other average values for different variables and compare the results to your original observations. To change the variable, select **PDP Variable:** located at the top of the Partial Dependence plot.
 
Learn more about Partial Dependence Plots with our [Machine Learning Interpretability Tutorial](https://h2oai.github.io/tutorials/machine-learning-interpretability-tutorial/#5).

5\. Explanations 

Explanations provide a detailed, easy-to-read **Reason Codes** for the top Global/Local Attributions.
1. Click on Explanations

![mli-dashboard-explanation](assets/mli-dashboard-explanation.jpg)

2. Determine the top 2 global attributions associated with 'survived.'

6\. Driverless AI offers other plots located under Driverless AI Model and Surrogate Models, take a few minutes to explore these plots; they are all interactive. **About this Plot** will provide an explanation of each plot.

Driverless AI Model
- Feature Importance
- Shapley
- Partial Dependence Plot
- Disparate Impact Analysis
- Sensitivity Analysis 

Surrogate Models
- KLime
- Random Forest
    - Feature Importance
    - Partial Dependency Plot
    - LOCO

7\. Click on the MLI link and learn more about "Machine Learning Interpretability with Driverless AI."

### Deeper Dive and Resources

- [Machine Learning, H2O.ai & Machine Learning  Interpretability | Interview with Patrick Hall](https://www.youtube.com/watch?v=TSmSBWnVSzc)

- [H2O Driverless AI Machine Learning Interpretability walkthrough]( 
https://www.youtube.com/watch?v=5jSU3CUReXY) (Oct 18)

- [Practical Tips for Interpreting Machine Learning Models - Patrick Hall, H2O.ai Youtube Video](https://www.youtube.com/watch?v=vUqC8UPw9SU) (June 18)

- [Practical Tips for Interpreting Machine Learning Models - Patrick Hall, H2O.ai Slideshare](https://www.slideshare.net/0xdata/practical-tips-for-interpreting-machine-learning-models-patrick-hall-h2oai)

- [Building Explainable Machine Learning Systems: The Good, the Bad, and the Ugly](https://www.youtube.com/watch?v=Q8rTrmqUQsU) (May 18)
 
- [An Introduction to Machine Learning Interpretability](https://www.oreilly.com/library/view/an-introduction-to/9781492033158/) 

- [Testing Machine Learning Explanation Techniques](https://www.oreilly.com/ideas/testing-machine-learning-interpretability-techniques)

- [Patrick Hall and H2O Github - Machine Learning with Python](https://github.com/jphall663/interpretable_machine_learning_with_python)

- [Patrick Hall and H2O Github - Machine Learning Interpretability](https://github.com/jphall663/awesome-machine-learning-interpretability) 

- [Download the Driverless AI MLI Cheat Sheet](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/_downloads/5cb84bc81a49817d5f490dde39bf42ee/cheatsheet.png) 

## Task 9: Experiment Summary and Autoreport

Driverless AI allows you to download auto-generated documents such as the Download Experiment Summary and the MLI Report, all at the click of a button. 

###  Experiment Summary

1\. Click on **Download Experiment Summary**

![download-experiment-summary](assets/download-experiment-summary.jpg)

When you open the zip file, the following files should be included:

- Experiment logs (regular and anonymized)
- A Summary of the Experiment
- Experiment Features along with relevant importance
- Ensemble information
- Experiment preview 
- Word version of an auto-generated report for the experiment
- Target transformations tuning leaderboard
- Tuning Leaderboard

2\. Open the auto-generated .doc report and review the experiment results.

3\. Click on **Download Autoreport**

![download-autoreport](assets/download-autoreport.jpg)

**Autoreport** is a Word version of an auto-generated report for the experiment. A report file (AutoDoc) is included in the experiment summary.

The zip file for the **Autoreport** provides insight into the following:

- Training data
- Any Detected Shifts in Distribution
- Validation Schema selected
- Model Parameter Tuning 
- Feature Evolution 
- Final set of Features chosen during the Experiment


### Deeper Dive and Resources

- [H2O.ai, Driverless AI Experiment Summary and Autoreport](http://docs.h2o.ai/driverless-ai/1-8-lts/docs/userguide/experiment-summary.html#autoreport)

- [Review this Webinar “Peek Under the Hood of H2O Driverless AI with Auto Doc”](https://www.brighttalk.com/webcast/16463/332693/peek-under-the-hood-of-h2o-driverless-ai-with-auto-doc) 

- [Try running an experiment without the Driverless AI UI using the Python Client](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/examples/h2oai_client_demo.html?highlight=experiment%20summary)

- [Toward AutoML for Regulated Industry with H2O Driverless AI](https://www.h2o.ai/blog/toward-automl-for-regulated-industry-with-h2o-driverless-ai/)

## Next Steps

Check out Driverless AI next tutorial [Machine Learning Experiment Scoring and Analysis Tutorial - Financial Focus](https://h2oai.github.io/tutorials/machine-learning-experiment-scoring-and-analysis-tutorial-financial-focus/#0)

Where you will learn how to:

- Evaluate a Driverless AI model through tools like:
	- ROC
	- Prec-Recall
	- Gain and Lift Charts
	- K-S Chart
	- Metrics such as:
	  - AUC
	  - F-Scores
	  - GINI
	  - MCC
	  - Log Loss
- Request a [21-Day Free Trial: H2O Driverless AI license Key](https://www.h2o.ai/products/h2o-driverless-ai/)

## Appendix: Project Workspace

Driverless AI provides a Project Workspace for managing datasets and experiments related to a specific business problem or use case. Whether you are trying to detect fraud or predict user retention, datasets, and experiments can be stored and saved in the individual projects. A Leaderboard on the Projects page allows you to easily compare performance and results and identify the best solution for your problem.

From the Projects page, you can link datasets and/or experiments, and you can run new experiments. When you link an existing experiment to a Project, the datasets used for the experiment will automatically be linked to this project (if not already linked).


### Explore an Existing Project Workspace


1\. Select **Projects** , an image similar to the one below will appear:
![projects-page](assets/projects-page.jpg)

*Things to Note:*

1. **Projects**: Projects Workspace for managing datasets and expirments menu option
2. Pre-created **Project** which includes:
    - **Name** : Project name (Time Series Tutorial)
    - **Description**: Optional (N/A)
    - **Train Datasets**: Number of train datasets (1)
    - **Valid Datasets**: Number of validation datasets (0)
    - **Test Datasets**: Number of test datasets (1)
    - **Experiments**: Number of experiments (1)
3. Additional options for the created project:
    - **Open**
    - **Rename**
    - **Delete**
4. **+New Project**: Option to create a new project 

3\. Open the **Time Series Tutorial**, an image similar to the one below will appear:
![projects-page-time-series](assets/projects-page-time-series.jpg)

*Things to Note:*

1. **Datasets** 
    - **Selected Datasets Type**: Training, Testing or Validation
    - Additional information on the dataset that was selected: Name, Rows, Columns

    ![projects-page-time-series-datasets](assets/projects-page-time-series-datasets.jpg)
    
    - **+ Link dataset** : Link an additional dataset (Training, Testing or Validation) to the existing project

2. **Experiments** 
    - **Select Scoring Dataset**: Select a test dataset to score using selected experiment
    - **Select Experiments**: Select any experiment for this project
    - **Select Scorer for Test Score**: Select a valid scorer for this experiment
    - **Score Dataset on Experiments**: Once you have selected the data for scoring, the scorer, and the model or models, you can begin the scoring process by clicking **Score Items**.
    - **Compare**: You can compare two or three experiments and view side-by-side detailed information about each.
    - **Unlink Items**: Unlink datasets and/or experiments
    - **+ Link Dataset**: Link an additional dataset to the experiment
    - **New Experiment**: Create a new experiment
    - Current linked experiment(s) info :
        - **Name**
        - **A**: Accuracy
        - **T** : Time
        - **I**: Interpretability
        - **Scorer**: Scorer used 
        - **Status**: In progress, completed
        - **Train Time**: Total time to train experiment
        - **Val. Score** : Validation score for the experiment
        - **Test Score**: Test score for the experiment
        - **Test Time**: Total time to test experiment 
 
 ### Create a Project Workspace

To create a Project Workspace:

1. Click the **Projects** option on the top menu
2. Click **New Project**
3. Specify a name for the project and provide a description
4. Click **Create Project**. This creates an empty Project page

- Learn more about projects in Driverless AI; check out the [Project Workspace Documentation](http://docs.h2o.ai/driverless-ai/latest-stable/docs/userguide/projects.html?highlight=projects%20workspace).

- A more extensive application of **Project Workspace** can be explored in the [Time Series Tutorial - Retail Sales Forecasting](https://h2oai.github.io/tutorials/time-series-recipe-tutorial-retail-sales-forecasting/#0). 
 

 
