Often the test distribution and train distribution can be different, so we shift the distribution to fit the new data


### **Covariate shift:**
The input distribution $P(x)$ changes, but the relationship between inputs and labels $P(y \mid x)$ stays the same. The data looks different but the underlying rule hasn't changed.

> Example: you train a cat detector on studio photos, but at test time you get phone camera photos. The cats are still cats, but the images look different.

### **Label shift:**
The label distribution $P(y)$ changes, but $P(x \mid y)$ stays the same. The underlying data looks the same per class, but the class frequencies shift.

> Example: you train on balanced data with 50% cats and 50% dogs, but at test time 90% are cats. The cats and dogs themselves look the same, just the proportions changed.

A useful way to remember the difference — covariate shift is about the **inputs changing**, label shift is about the **class frequencies changing**.


![[Pasted image 20260603233947.png]]