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
  * RNN 은 vanishing gradient 현상이 나타나기 쉽지만, LSTM 은 이를 보완하기 위해 Cell state를 사용하였습니다.
  * RNN 이 vanishing gradient 현상이 나타나기 쉬운 이유는 input 값이 매우 길어져서 dimension이 매우 늘어나기 때문에 발생합니다.
  * 반면 LSTM 은 Cell state 에 필요한 정보를 끝까지 남겨놓음으로써 vanishing gradient 를 줄이고 있습니다.
