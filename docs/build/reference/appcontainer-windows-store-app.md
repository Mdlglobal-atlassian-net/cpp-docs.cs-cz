---
title: / APPCONTAINER (aplikace pro UPW/Microsoft Store)
ms.date: 11/04/2016
ms.assetid: 9a432db5-7640-460b-ab18-6f61fa7daf6f
ms.openlocfilehash: f7ab8cf1ce034580953fdf1403264e8ef3d3ff09
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812405"
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

1. Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **Linkeru** uzlu.

1. Vyberte **příkazového řádku** stránku vlastností.

1. V **další možnosti**, zadejte `/APPCONTAINER` nebo `/APPCONTAINER:NO`.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
