# J-type

<figure><img src="../../.gitbook/assets/j-type.png" alt=""><figcaption></figcaption></figure>

## JALR (I-Format)

{% hint style="warning" %}

I'm sorry for putting JALR here. Actually JALR is I-type.

{% endhint %}

<figure><img src="../../.gitbook/assets/jalr.png" alt=""><figcaption></figcaption></figure>

* `JARL rd, rs1, imm`
  * Reg[rd] <- PC + 4; PC <- Reg[rs1] + imm;
    * Write `PC + 4` to Reg[rd] (*return address*)
    * Sets PC = Reg[rs1] + offset

{% hint style="warning" %}

Don't need to multiply the immediate by 2.

{% endhint %}


### Adding `JALR` to datapath

<figure><img src="../../.gitbook/assets/datapath6.jpg" alt=""><figcaption></figcaption></figure>

## JAL

<figure><img src="../../.gitbook/assets/jal.png" alt=""><figcaption></figcaption></figure>

### Adding `JAL` to datapath

{% hint style="info" %}

What should be added to datapath?

{% endhint %}
