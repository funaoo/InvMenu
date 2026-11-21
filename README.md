# InvMenu

[Muqsit's InvMenu](https://github.com/Muqsit/InvMenu) for PocketMine-MP, as included in [MultiVersion-Altay](https://github.com/funaoo/MultiVersion-Altay).

The code is the same as the original. It lives at `src/libs/muqsit/invmenu` under the namespace `libs\muqsit\invmenu`.

## Usage

Register the handler once from your plugin, then create menus:

```php
use libs\muqsit\invmenu\InvMenu;
use libs\muqsit\invmenu\InvMenuHandler;
use libs\muqsit\invmenu\transaction\InvMenuTransaction;
use libs\muqsit\invmenu\transaction\InvMenuTransactionResult;

// in onEnable()
if(!InvMenuHandler::isRegistered()){
    InvMenuHandler::register($this);
}

$menu = InvMenu::create(InvMenu::TYPE_CHEST);
$menu->setName("My menu");
$menu->setListener(function(InvMenuTransaction $transaction) : InvMenuTransactionResult{
    return $transaction->discard(); // cancels the item movement
});
$menu->send($player);
```

Available types: `TYPE_CHEST`, `TYPE_DOUBLE_CHEST` and `TYPE_HOPPER`.

## Using it with MultiVersion-Altay

[MultiVersion-Altay](https://github.com/funaoo/MultiVersion-Altay) already includes this InvMenu and registers it on startup. It is recommended to use that copy, especially for players on 0.15.10. In that case, add `depend: [MultiVersion]` to your plugin and do not register or bundle InvMenu again.

## Credits

- [Muqsit/InvMenu](https://github.com/Muqsit/InvMenu): the original InvMenu.
