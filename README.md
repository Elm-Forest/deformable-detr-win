# Deformable DTER for windows
Deformable DTER for windows and includes a reasoning implementation of Deformable DTER

![deformable_detr](./figs/illustration.png)

When I tried to test [Deformable DETR](https://github.com/fundamentalvision/Deformable-DETR) on windows, I found that I could not import `MultiScaleDeformableAttention`. \
So I followed the instructions to execute `make.sh`, but it did not work. \
After checking the source code I found that the underlying `MultiScaleDeformableAttention` is written in **c++**.\
So I configured the `clang` environment to compile the **c++** files in the project and it finally worked.\
The process was unquestionably a headache, so for your convenience I've brought the compiled project here and created a notebook for you to use for Deformable DETR reasoning. \
Here it is [deformable_detr](https://github.com/Elm-Forest/deformable-detr-win/blob/master/deformable_detr.ipynb) 

<div align=center>
  <img src='https://user-images.githubusercontent.com/62285254/200105820-8c8cdb82-7641-4ed2-8c23-67afce5c15e5.png' width='50%'>
</div>

### Preparation
Download the [Deformable DETR weights](https://drive.google.com/file/d/1nDWZWHuRwtwGden77NLM9JoWe-YisJnA/view?usp=sharing) ,and put it in the root content\
And if you want to try other weights ,here it is


| <sub><sub>Method</sub></sub>   | <sub><sub>Epochs</sub></sub> | <sub><sub>AP</sub></sub> | <sub><sub>AP<sub>S</sub></sub></sub> | <sub><sub>AP<sub>M</sub></sub></sub> | <sub><sub>AP<sub>L</sub></sub></sub> | <sub><sub>params<br>(M)</sub></sub> | <sub><sub>FLOPs<br>(G)</sub></sub> | <sub><sub>Total<br>Train<br>Time<br>(GPU<br/>hours)</sub></sub> | <sub><sub>Train<br/>Speed<br>(GPU<br/>hours<br/>/epoch)</sub></sub> | <sub><sub>Infer<br/>Speed<br/>(FPS)</sub></sub> | <sub><sub>Batch<br/>Infer<br/>Speed<br>(FPS)</sub></sub> | <sub><sub>URL</sub></sub>                     |
| ----------------------------------- | :----: | :--: | :----: | :---: | :------------------------------: | :--------------------:| :----------------------------------------------------------: | :--: | :---: | :---: | ----- | ----- |
| **<sub><sub>Deformable DETR<br>(single scale)</sub></sub>** | <sub>50</sub> | <sub>39.4</sub> | <sub>20.6</sub> | <sub>43.0</sub> | <sub>55.5</sub> | <sub>34</sub> |<sub>78</sub>|<sub>160</sub>|<sub>3.2</sub>|<sub>27.0</sub>|<sub>42.4</sub>| <sub>[config](./configs/r50_deformable_detr_single_scale.sh)<br/>[log](https://drive.google.com/file/d/1n3ZnZ-UAqmTUR4AZoM4qQntIDn6qCZx4/view?usp=sharing)<br/>[model](https://drive.google.com/file/d/1WEjQ9_FgfI5sw5OZZ4ix-OKk-IJ_-SDU/view?usp=sharing)</sub> |
| **<sub><sub>Deformable DETR<br>(single scale, DC5)</sub></sub>** | <sub>50</sub> | <sub>41.5</sub> | <sub>24.1</sub> | <sub>45.3</sub> | <sub>56.0</sub> | <sub>34</sub> |<sub>128</sub>|<sub>215</sub>|<sub>4.3</sub>|<sub>22.1</sub>|<sub>29.4</sub>| <sub>[config](./configs/r50_deformable_detr_single_scale_dc5.sh)<br/>[log](https://drive.google.com/file/d/1-UfTp2q4GIkJjsaMRIkQxa5k5vn8_n-B/view?usp=sharing)<br/>[model](https://drive.google.com/file/d/1m_TgMjzH7D44fbA-c_jiBZ-xf-odxGdk/view?usp=sharing)</sub> |
| **<sub><sub>Deformable DETR</sub></sub>** | <sub>50</sub> | <sub>44.5</sub> | <sub>27.1</sub> | <sub>47.6</sub> | <sub>59.6</sub> | <sub>40</sub> |<sub>173</sub>|<sub>325</sub>|<sub>6.5</sub>|<sub>15.0</sub>|<sub>19.4</sub>|<sub>[config](./configs/r50_deformable_detr.sh)<br/>[log](https://drive.google.com/file/d/18YSLshFjc_erOLfFC-hHu4MX4iyz1Dqr/view?usp=sharing)<br/>[model](https://drive.google.com/file/d/1nDWZWHuRwtwGden77NLM9JoWe-YisJnA/view?usp=sharing)</sub>                   |
| **<sub><sub>+ iterative bounding box refinement</sub></sub>** | <sub>50</sub> | <sub>46.2</sub> | <sub>28.3</sub> | <sub>49.2</sub> | <sub>61.5</sub> | <sub>41</sub> |<sub>173</sub>|<sub>325</sub>|<sub>6.5</sub>|<sub>15.0</sub>|<sub>19.4</sub>|<sub>[config](./configs/r50_deformable_detr_plus_iterative_bbox_refinement.sh)<br/>[log](https://drive.google.com/file/d/1DFNloITi1SFBWjYzvVEAI75ndwmGM1Uj/view?usp=sharing)<br/>[model](https://drive.google.com/file/d/1JYKyRYzUH7uo9eVfDaVCiaIGZb5YTCuI/view?usp=sharing)</sub> |
| **<sub><sub>++ two-stage Deformable DETR</sub></sub>** | <sub>50</sub> | <sub>46.9</sub> | <sub>29.6</sub> | <sub>50.1</sub> | <sub>61.6</sub> | <sub>41</sub> |<sub>173</sub>|<sub>340</sub>|<sub>6.8</sub>|<sub>14.5</sub>|<sub>18.8</sub>|<sub>[config](./configs/r50_deformable_detr_plus_iterative_bbox_refinement_plus_plus_two_stage.sh)<br/>[log](https://drive.google.com/file/d/1ozi0wbv5-Sc5TbWt1jAuXco72vEfEtbY/view?usp=sharing) <br/>[model](https://drive.google.com/file/d/15I03A7hNTpwuLNdfuEmW9_taZMNVssEp/view?usp=sharing)</sub> |
