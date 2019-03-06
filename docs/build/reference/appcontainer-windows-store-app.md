---
title: / APPCONTAINER (aplikace pro UPW/Microsoft Store)
ms.date: 11/04/2016
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
ms.openlocfilehash: c58559a908a9281507c74c2dd3ff7e56490cb6e3
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418669"
---
# <a name="appcontainer-microsoft-store-app"></a>/ APPCONTAINER (aplikace pro Microsoft Store)

Určuje, zda linker vytvoří spustitelný obraz, který musí být spuštěn v kontejneru aplikace.

## <a name="syntax"></a>Syntaxe

```
/APPCONTAINER[:NO]
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je/appcontainer vypnut.

Tato možnost změní spustitelný soubor k označení, zda je třeba aplikaci spustit v prostředí izolace procesu appcontainer. Určit/appcontainer pro aplikaci, která se musí spustit v prostředí appcontainer, například univerzální platformu Windows (UPW) nebo Windows Phone 8.x aplikace. (Možnost je nastavena automaticky v sadě Visual Studio při vytváření aplikace Universal Windows ze šablony.) Pro desktopové aplikace zadejte /APPCONTAINER:NO nebo možnost jednoduše vynechejte.

Možnost/appcontainer byla zavedena v systému Windows 8.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **příkazového řádku** stránku vlastností.

1. V **další možnosti**, zadejte `/APPCONTAINER` nebo `/APPCONTAINER:NO`.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
