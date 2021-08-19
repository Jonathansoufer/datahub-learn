# 4. Check the account balance

## SOL Token balances

We must check the account balance to make sure we have sufficient `SOL` to perform a transfer. The `getBalance()` function takes a publicKey as input and will return the balance associated with that publicKey, if there is any.

## The challenge

>In `pages/api/solana/balance.ts`, implement `balance`.

**Need some help?** Here are a few hints
* [Read about getBalance](https://solana-labs.github.io/solana-web3.js/classes/Connection.html#getbalance)

Take a few minutes to figure this out.

```typescript
//...
    const address = req.body.address as PublicKey;
    const url = getSafeUrl();
    const connection = new Connection(url);
    const publicKey =undefined;
    const balance = undefined;
    res.status(200).json(balance);
//...
```

> You can also [**join us on Discord**](https://discord.gg/fszyM7K) if you have questions.

Still not sure how to do this? No problem! The solution is below so you don't get stuck.

## The solution

```typescript
//...
    const address = req.body.address as PublicKey;
    const url = getSafeUrl();
    const connection = new Connection(url);
    const publicKey = new PublicKey(address);
    const balance = await connection.getBalance(publicKey);
    res.status(200).json(balance);
//...
```

**What happened in the code above?**

* We create a `PublicKey` using the string formated address
* We call `connection.getBalance` with that `publicKey`
* Be aware than the balance is on `LAMPORTS` (`console.log` is your friend ^^) 

Enter the address you just funded and click on **Check Balance**. You should see:

![](https://github.com/figment-networks/datahub-learn/blob/master/.gitbook/assets/solana-balance.png)

## Next

Now that we have an account and that this account has been funded with SOL tokens, we are ready to make a transfer!