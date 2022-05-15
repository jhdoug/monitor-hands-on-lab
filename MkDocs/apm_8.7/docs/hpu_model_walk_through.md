
# HPU ST model walk through

- Juan Gu - <gujuan@ibm.com>

In this exercise, user can understand how the model works in hpu, and some examples of customization on ootb notebooks.

**Pre-requisites**

Ensure you have access to :<br> 
- MAS v8.7 Health and Predict Utilities<br> 
- HPU dataloader URL<br> 
- Waston studio access<br> 
- Sample ST(Substation Transformer) data for hpu, and make sure required data are loaded through dataloader via App Connect. Check out the sample data folder structure as below.<br> 
![drawing](/img/apm_8.7/hpu_model_st_sample_data_overview.png){ width=70% height=70% }<br>   

Where to put the sample data??

## Health and Predict Utilities out of the box models

Supported Asset classes listed in below table.


|  Asset class  | Model |
|--|--|
| DISTRIBUTION TRANSFORMER | IBM Transformers Tap Changers 4.0.0 |
| SUBSTATION TRANSFORMER | IBM Transformers Tap Changers 4.0.0,IBM Transformers Tap Changers DGA 4.0.0 |
| INSTRUMENT TRANSFORMER   | IBM Instrument Transformers Oil Filled CTs 4.0.0 |
| SWITCHGEAR | IBM Gas Insulated Switchgear 4.0.0 |
| UNDERGROUND TRANSMISSION MANHOLE | IBM Underground Transmission Manholes 4.0.0 |
| METAL SUPPORT STRUCTURE | IBM Metal Support Structures 4.0.0 |
| OVERHEAD TRANSMISSION WIRE| IBM Conductors 4.0.0 |
| POLE -  Wood Power Pole | IBM Wood Pole Structures 4.0.0 |
| CIRCUITBREAKER - Oil Circuit Breaker | IBM Circuit Breakers Oil 4.0.0 |
| CIRCUITBREAKER - Air Blast Circuit Breaker | IBM Circuit Breakers Air Blast 4.0.0 |
| CIRCUITBREAKER - Air Magnetic Circuit Breaker | IBM Circuit Breakers Air Magnetic 4.0.0 |
| CIRCUITBREAKER - Vacuum Circuit Breaker | IBM Circuit Breakers Vacuum 4.0.0 |
| CIRCUITBREAKER - SF6 Circuit Breaker | IBM Circuit Breakers SF6 4.0.0 |
| UNDERGROUNDTRANSMISSIONCABLE - High Pressure Fluid Filled Pipe Type (HPFF) Cables | IBM HPFF Cables 4.0.0 |
| UNDERGROUNDTRANSMISSIONCABLE - Mass Impregnated (MI) Cables | IBM MI Cables 4.0.0 |
| UNDERGROUNDTRANSMISSIONCABLE - Self Contained Fluid Filled (SCFF) Cables | IBM SCFF Cables 4.0.0 |
| UNDERGROUNDTRANSMISSIONCABLE - Self Contained Gas Filled (SCGF) Submarine Cables | IBM SCGF Cables 4.0.0 |
| UNDERGROUNDTRANSMISSIONCABLE - Extruded Cross Linked Polyethylene (XLPE) Cables | IBM XLPE Cables 4.0.0 |


**Note**, some asset classes have subtype, like CIRCUITBREAKER or UNDERGROUNDTRANSMISSIONCABLE


## Create a score group for ST assets
1. Login and go to Health and Predict Utilities application.
![drawing](/img/apm_8.7/hpu_model_sc_setup_0.png){ width=100% height=100% }<br>   

2. Click `Scoring and DGA settings` in the menu,in Scoring and DGA settings page, click `Create a scoring and DGA group` button.
![drawing](/img/apm_8.7/hpu_model_sc_setup_1.png){ width=100% height=100% }<br>   

3. In the create score group page,fill in name,description, select `Asset` object,choose `Connectigng group to notebook`.

    Then click `Select` to choose `IBM Transformers Tap Changers DGA 4.0.0` notebook in the notebook list dialog,click `Use notebook`.
    ![drawing](/img/apm_8.7/hpu_model_sc_setup_2.png){ width=100% height=100% }<br>   

    Scroll down `query` part, click `Select` to open query dialog, user can select an existing query, or click `+` button to create a new query for ST assets.
    ![drawing](/img/apm_8.7/hpu_model_sc_setup_3.png){ width=100% height=100% }<br>   
    ![drawing](/img/apm_8.7/hpu_model_sc_setup_4.png){ width=100% height=100% }<br>   

    After select the notebook and query, click `Create` to create the score group.
    ![drawing](/img/apm_8.7/hpu_model_sc_setup_5.png){ width=100% height=100% }<br>   

4. After score group is created, system will redirect to the score group detail page, in this page, user can see all the scores and the asset list.
    ![drawing](/img/apm_8.7/hpu_model_sc_setup_6.png){ width=100% height=100% }<br>   

    Click the score in the table, and active it on the right, scores need to be activated one by one based on the depedency.
    ![drawing](/img/apm_8.7/hpu_model_sc_setup_7.png){ width=100% height=100% }<br>   
    ![drawing](/img/apm_8.7/hpu_model_sc_setup_8.png){ width=100% height=100% }<br>   

5. After activing all the scores, click the `Recalculate scores` to start the analysis.


## Watson Studio notebooks and jobs
In hpu, the calculation happens in the jobs in Watson Studio. Each asset type has a configure file, notebook, and job deployed on Watson Studio project. When user clicks `Recalculate scores` on UI, it triggers the job to run, do the calculation, and save results to DB.<br> 
For example, for ST(Substation Transformer), configuration file is IBM-Transformers-Tap-Changers-DGA-4.0.0.cfg, notebook is IBM-Transformers-Tap-Changers-DGA-4.0.0.ipynb, job is Run-IBM-Transformers-Tap-Changers-DGA-4-0-0
![drawing](/img/apm_8.7/hpu_model_ws_cfg.png){ width=100% height=100% }<br>  
![drawing](/img/apm_8.7/hpu_model_ws_notebook.png){ width=100% height=100% }<br>   
![drawing](/img/apm_8.7/hpu_model_ws_job.png){ width=100% height=100% }<br>   

### Customize notebook model, like DGA, NOC



### Enable debug mode

### Run notebook directly for debug purpose







