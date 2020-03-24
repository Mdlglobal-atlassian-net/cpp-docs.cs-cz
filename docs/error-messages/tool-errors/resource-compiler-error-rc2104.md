---
title: Chyba kompilátoru prostředků RC2104
ms.date: 11/04/2016
f1_keywords:
- RC2104
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
ms.openlocfilehash: d4a06f88e4a73da6b711d108a1f79c14fae0907c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191636"
---
# <a name="resource-compiler-error-rc2104"></a>Chyba kompilátoru prostředků RC2104

nedefinované klíčové slovo nebo název klíče: klíč

Zadané klíčové slovo nebo název klíče nejsou definovány.

Tato chyba je často způsobena překlepem v definici prostředků nebo v zahrnutém souboru hlaviček. Může to být také způsobeno chybějící hlavičkovým souborem.

Chcete-li tento problém vyřešit, vyhledejte hlavičkový soubor, který by měl obsahovat definované klíčové slovo nebo klíč, a ověřte, zda je obsažen v souboru prostředků a zda je klíčové slovo nebo název klíče zadán správně. Pokud byl projekt vytvořen s předkompilovanou hlavičkou a následně jej odeberete, ujistěte se, že soubor prostředků stále obsahuje povinná záhlaví.

Chcete-li ověřit definovaná klíčová slova a názvy klíčů v souboru prostředků, v aplikaci Visual Studio otevřete okno **prostředky** – na panelu nabídek zvolte možnost **zobrazení**, **prostředky**a pak otevřete místní nabídku pro soubor. RC a zvolte možnost **symboly prostředků** , chcete-li zobrazit seznam definovaných symbolů. Chcete-li upravit zahrnuté hlavičky, otevřete místní nabídku pro soubor. RC a vyberte možnost **prostředek zahrnuje**.

Pokud narazíte na tuto zprávu:

```
undefined keyword or key name: MFT_STRING
```

Otevřete \MCL\MFC\Include\AfxRes.h a přidejte tuto direktivu include:

```
#include <winresrc.h>
```
