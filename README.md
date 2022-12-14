![header](https://capsule-render.vercel.app/api?type=waving&color=auto&height=200&text=Welcome!%20&fontSize=60&fontAlignY=40&desc=I'm%20joonho)

$$\theta^*_\tau \leftarrow \mathcal{A_\phi}(\mathcal{L}_\tau,\mathcal{D}_\tau^{\text{train}},\mathcal{f}_\theta)$$

$$m(\theta^*_\tau)\leftarrow \mathcal{P}_\tau(\mathcal{D}_\tau^{\text{valid}},\mathcal{f}_\theta_\tau)$$

### pytorch_summary1
* tensor 생성 ( torch.ones, torch.rand_like, torch.arange )
  * torch.rand 와 torch.randn 의 차이점 
    * torch.rand는 골고루 퍼져있는 분포를 나타냅니다.
    * torch.randn 은 가우시안 정규분포를 나타냅니다.
* tensor 연산 ( sum, mean )
* tensor 조작 ( reshape, torch.cat(dim=0(row) dim=1(columns), squeeze, unsqueeze )

### pytorch_summary2
* CNN layer 커스텀
  * layer의 층이 많아 지는 것보다 깊이를 깊게 하는 것이 성능이 더 잘 나올 수 있습니다.
  * Batch Normalization 을 하면 성능이 좋아집니다. (단, layer만 많으면 효과가 없음)
  * pooling 의 유무에 따라 성능, 속도에서 차이가 많이 납니다. (있는게 훨씬 좋음)
  * dropout는 BN을 사용해서인지 드라마틱한 성능을 보이진 않았습니다.
  * learing rate 에 따라 성능차이가 확연히 차이납니다.

### pytorch_summary3
* U-net 을 구현해보고 skip connection 이해
  * skip connection 은 concat 과 add 두가지 방식이 있습니다.
  * U-net 은 concat 을 사용하기 때문에, up-conv를 할때 dimension을 줄어야 합니다.
  * 그래야 concat 했을 때 원래 차원의 사이즈를 가질 수 있기 때문입니다.
   * Residual Learning : x를 input으로 하여 output도 자기자신(x)을 타겟으로 할때, skip Connection(add방식)을 하면 성능이 빠르게 좋아집니다.
   * 3x3 kernel의 주변 값이 매우 작게 되어 빠르게 더 좋은 성능을 이끌어 낼수 있기 때문입니다.
 * Transposed Convolution (확장)방식에 대한 이해 (각각의 커널값을 행렬곱하여 계산)

### pytorch_summary4
* RNN 과 LSTM 을 실습과 이해
  * RNN 은 vanishing gradient 현상이 나타나기 쉽지만, LSTM 은 이를 보완하기 위해 Cell state를 사용합니다.
  * RNN 이 vanishing gradient 현상이 나타나기 쉬운 이유는 input 값이 매우 길어져서 dimension이 매우 늘어나기 때문에 발생합니다.
  * 반면 LSTM 은 Cell state 에 필요한 정보를 끝까지 남겨놓음으로써 vanishing gradient 를 줄이고 있습니다.
  
### pytorch_summary5
* Transformer 구조 이해(self-attention, attention 구조)
  * attention이란 한번에 입력된 sequence를 서로의 유사성을 통해 가중치를 부여하는 것입니다.
  * Encoder 와 Decoder 로 나누어져 있습니다.
* Encoder :
   * Encoder 는 positional encoding (위치정보) 를 거쳐 key, query, value 로 Multi-Head attention 에 들어갑니다.
   * skip connection 을 통해 attention value 와 add 와 Norm 을 거쳐 Feed Foward를 해줍니다.
   * Feed Forwad --> skip connection --> add&norm --> decoder 의 multi-head attention(value, key)
* Decoder :
   * Output Embedding --> positional encoding --> masked Multi-Head Attention --> skip connection(add&norm)
   * --> Multi-head Attention(input : encoder 의 value, key decoder 의 query) --> add&norm --> Feed Forward-->add&norm-->Linear -->softmax
   * masked Multi-Head Attention 을 쓰는 이유는 한번에 입력된 sequence의 뒷부분을 치팅학습 하는 것을 방지하기 위해서입니다.
   
### pytorch_summary6
* 추천시스템의 이해
* Content-based Filtering
  * 장점
    * 유저가 구매, like, watch 했던 자료를 기반으로 추천하는 시스템입니다.
    * 유저 개인의 자료만 중요(다른 유저의 자료는 필요 없음) 합니다.
    * 유저 개인의 취향에 맞춰서 추천할 수 있습니다.
    * 신제품 같은 구매이력이 없는 것도 추천 가능합니다.
  * 단점
    * 유저의 특징을 추출하는 작업 자체가 어렵습니다. (이미지, 음악 등)
    * 추천 편향이 생깁니다. 특히 추천하기 어려운 나쁜 퀄리티까지 추천될 가능성이 높습니다.
 
* Collaborative Filtering
  * 장점
    * 다른 유저의 패턴을 고려하여 추천하는 시스템입니다.
    * 콘텐츠에서 특징을 뽑을 작업이 필요 없습니다. (다른 유저의 패턴을 고려하므로)
  * 단점
    * 충분한 유저의 자료가 있어야 비교가 가능합니다.
    * 누구도 구매한 적이 없는 신상제품은 추천이 어렵습니다.
    * 유저 개인의 독특한 취향을 적용하기 어렵습니다. 결국 인기상품의 추천이 될 가능성이 있습니다.
  
  
* Hybrid Filtering
  * 위 두가지 방법을 조합한 시스템입니다.
  * 단순 예측 결과를 합치는 방법, 다른 하나를 보완하는 방법, 하나의 모델로 합치는 방법 등이 있습니다.
 
* DeepFM
 * Deep -> Deep Neural Network,    FM --> Factorization Machine
 * FM Machine part
   * Sparse Feature(1,0,0,...) --> Embeding --> FM layer(inner Product) --> sigmoid function(output)
 * DNN part 
   * Sparse Feature(1,0,0,...) --> Embeding --> hidden layer --> sigmoid function(output)
 * FM 에서 사용했던 Embeding size 를 DNN Embeding 에도 사용하여 동시에 작업이 가능한 것이 특징입니다.
 
 
  
