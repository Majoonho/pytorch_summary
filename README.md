![header](https://capsule-render.vercel.app/api?type=waving&color=auto&height=200&text=Welcome!%20&fontSize=60&fontAlignY=40&desc=I'm%20joonho)

$$\theta^*_\tau \leftarrow \mathcal{A_\phi}(\mathcal{L}_\tau,\mathcal{D}_\tau^{\text{train}},\mathcal{f}_\theta)$$

$$m(\theta^*_\tau)\leftarrow \mathcal{P}_\tau(\mathcal{D}_\tau^{\text{valid}},\mathcal{f}_\theta_\tau)$$

### pytorch_summary1
* tensor 생성 ( torch.ones, torch.rand_like, torch.arange )
  * torch.rand 와 torch.randn 의 차이점 
    * torch.rand는 골고루 퍼져있는 분포를 나타낸다.
    * torch.randn 은 가우시안 정규분포를 나타낸다.
* tensor 연산 ( sum, mean )
* tensor 조작 ( reshape, torch.cat(dim=0(row) dim=1(columns), squeeze, unsqueeze )

