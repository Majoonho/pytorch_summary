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

