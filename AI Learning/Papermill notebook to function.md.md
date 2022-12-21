# Convert Jupyter Notebooks into Functions
[link](https://towardsdatascience.com/convert-jupyter-notebooks-into-functions-6fbda7b18419)
### Papermill: Parameterize and execute Jupyter notebooks automatically
```
pip install papermill[all]
papermill hello_papermill.ipynb output.ipynb -p a 10 -p b 20
papermill plot_stock_price.ipynb output_TSLA.ipynb -p stock 'TSLA'
```
1. Create a Jupyter notebook in your Desktop and name it `hello_papermill` 
2. Say, we want to parameterize _a_ and _b_ to calculate `a+b`. We will create this code block.
![](https://miro.medium.com/max/700/1*9uJEpfp67qPWFGJmd5HKEA.png)

3. Go to the toolbar -> View -> Cell Toolbar -> Tags.

![](https://miro.medium.com/max/700/1*3-M_D0U0SmbGJce3rCR6_A.png)

4. Type `parameters`to top-right corner of the first cell. Click ‘Add tag’. The notebook is parameterized!

![](https://miro.medium.com/max/700/1*iZ4aGLGLNeFYRoStZkbkKw.png)

5. Start a terminal and navigate to your Desktop.
```
papermill ./predict_linear_regression.ipynb ./predict_output2.ipynb -p input_name './input_set2.csv' -p output_name './output_set2.csv'


```
Alternative 2: In Jupyter, navigate to the directory containing `predict_linear_regression.ipynb`. Create a new notebook there and run the command.
```
import papermill as pm  
  
pm.execute_notebook(  
   'predict_linear_regression.ipynb',  
   'predict_output2.ipynb',  
   parameters = {'input_name': './input_set2.csv',   
                 'output_name': './output_set2.csv')
```

```
$ papermill predict_linear_regression.ipynb s3://bkt/output.ipynb -p alpha 0.6 -p l1_ratio 0.1

$ papermill predict_linear_regression.ipynb s3://bkt/output.ipynb -f parameters.yaml
```

# 6. More resources for Papermill

-   Netflix published how they use Papermill to [automatically execute notebooks daily](https://netflixtechblog.com/notebook-innovation-591ee3221233) for data analytics and engineering work.
-   Read the [documentation](https://github.com/nteract/papermill) for a clearer idea of how it works.



# NetFlix:
We’ve also built a rich ecosystem of complementary tools and services, such as [Genie](https://medium.com/netflix-techblog/evolving-the-netflix-data-platform-with-genie-3-598021604dda), a federated job execution service, and [Metacat](https://medium.com/netflix-techblog/metacat-making-big-data-discoverable-and-meaningful-at-netflix-56fb36a53520), a federated metastore. These tools simplify the complexity, making it possible to support a broader set of users across the company.


**data exploration —** occurs early in a project; may include viewing sample data, running queries for statistical profiling and exploratory analysis, and visualizing data

**data preparation** — iterative task; may include cleaning, standardizing, transforming, denormalizing, and aggregating data; typically the most time-intensive task of a project

**data validation** — recurring task; may include viewing sample data, running queries for statistical profiling and aggregate analysis, and visualizing data; typically occurs as part of data exploration, data preparation, development, pre-deployment, and post-deployment phases

**productionalization** — occurs late in a project; may include deploying code to production, backfilling datasets, training models, validating data, and scheduling workflows

