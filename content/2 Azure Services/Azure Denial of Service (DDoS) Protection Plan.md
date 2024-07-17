> [!caution]
> This is a paid resource, refer to the footnotes section for more information[^1].

There are two types of DDoS protection:
- Per IP Protection plan which is configured in [[Azure Public IP Address]]
- [[Azure Denial of Service (DDoS) Protection Plan]] which protects all resources within a Subscription, this post will cover setting up this plan

Navigate to the DDoS protection plan in the Azure portal. 

Select Create DDos protection plan:

![[Pasted image 20240717111935.png]]

Select the resource group you want to protect and select the region:

![[Pasted image 20240717112348.png]]

Select Review + create, once done you will be able to protect all your resources in a subscription. 

[^1]: Refer to the pricing for further details:
https://azure.microsoft.com/en-us/pricing/details/ddos-protection/
