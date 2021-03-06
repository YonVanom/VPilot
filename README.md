# VPilot
Keras Deep Learning project to build a self-driving agent that takes camera frames as input and predicts steering, throttle and brake commands, trained using the [DeepGTAV](https://github.com/ai-tor/DeepGTAV) self-driving car development environment.

<img src="http://forococheselectricos.com/wp-content/uploads/2016/07/tesla-autopilot-1.jpg" alt="Self-Driving Car" width="900px">

## How it works

VPilot uses a LRCN (Convolutional Recurrent Neural Network) as self-driving agent, see _model.py_. It is based on the [NVIDIA's autosteering CNN](https://arxiv.org/abs/1604.07316) and [Long-term Recurrent Convolutional Networks](https://arxiv.org/abs/1411.4389) insights. LSTM is used to include also temporal inference in the network, which I believe will help the agent to accurately predict throttle and brake actions also, which contrary to steering angle, are difficult to deduce from single frames.

Training is still in progress and so weights are not yet provided. However _train.py_ is provided to be able to easily apply supervised learning with a dataset generated by DeepGTAV. You just need to change the dataset directories list.

Once proper weights are generated, _drive.py_ can be used to test your agent, allowing DeepGTAV to connect to your model in Reinforcement Learning mode. Once the game is loaded, _drive.py_ will take the current frame from the game, run it through the LRCN and send the output commands back to GTAV and so the vehicle should start moving, hopefully like a real self-driving car :). Don't forget the set the correct arguments when running the script!
