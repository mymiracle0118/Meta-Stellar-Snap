# Metastellar FAQ
Please See if your question is anwsered by the FAQ


<div style="width:50%; height:0; padding-bottom:100%; position:relative;"><div style="width:100%;height:0;padding-bottom:100%;position:relative;"><iframe src="https://giphy.com/embed/XZyZJCtQHo7dPGWjG2" width="100%" height="100%" style="position:absolute" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></div><p><a href="https://giphy.com/gifs/netflix-duncan-trussell-midnight-gospel-the-XZyZJCtQHo7dPGWjG2">via GIPHY</a></p>
</div>
If not you can send an email to
<b>support@metastellar.io</b>

<div class="spacer"></div>

# Wallet

------------------------------------------- 

## Install

to install the Stellar-Snap

1. Make sure you have the latest version of the <b>Metamask Browser extension</b>, it can be installed [here](https://metamask.io/download/)
2. After metamask is installed

<button id="installButton">Install MetaStellar</button>

<br>
<div class="appearOnConnected">
<p>You can test you're installation with</p>
<br>
<button id="viewAddress">Test Install</button>
</div>

<div class="spacer"></div>

## Wallet Support 💳

## how do I access my Wallet

## Where are my keys located?

## How do I export my account?

## How do I import an account?

## How can I see my stellar address?

## Can I use this on my phone?

# Metamask Support


snap support
<b>support@metastellar.io</b>

metamask

<script>
    console.log("script live");
let metastellarButton = document.getElementById("installButton");
metastellarButton.addEventListener('click', async ()=>await connectSnap());

let viewAddress = document.getElementById('viewAddress');
viewAddress.addEventListener('click', async ()=>await displayAddress());

function setConnected(connected){
    let display = connected? 'block' : 'none'
    let elements = document.getElementsByClassName('appearOnConnected');
    for(let i = 0; i<elements.length; i++){
        elements[i].style.display = display
    }
}

setConnected(false);

async function connectSnap(){
    try{
        console.log("here")
        const connected = await ethereum.request({
        method: 'wallet_requestSnaps',
        params: {
            ['npm:stellar-snap']: {}
        },
        });
        console.log(connected)
        setConnected(true)
        return true;
    }catch(e){
        if (e.toString() === "ReferenceError: ethereum is not defined"){
            alert("Install Metamask")
        }
        alert(e);
        setConnected(false);
        return false;
    }
}


async function displayAddress(){
    try{
    const request = {
        method: 'wallet_invokeSnap',
        params: {snapId:`npm:stellar-snap`, 
            request:{
                method: `${'showAddress'}`
            }
            }
        }
    let address = await ethereum.request(request);
    }
    catch(e){
        alert(e);
    }
}

</script>