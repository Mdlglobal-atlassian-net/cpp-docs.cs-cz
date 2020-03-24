---
title: Upozornění příkazového řádku D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 7c685a1ca3195ad4ab52bab8b5d32b1a51534b24
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196572"
---
# <a name="command-line-warning-d9041"></a>Upozornění příkazového řádku D9041

Neplatná hodnota Value pro/Option; Předpokládá se hodnota "value"; Při zadání tohoto upozornění přidat do možností příkazového řádku '/Analyze '

Číslo upozornění analýzy kódu bylo přidáno do možnosti příkazového řádku **/WD**, **/We**, **/WO**nebo **/WL** bez určení možnosti příkazového řádku **/analyze** . Chcete-li tuto chybu vyřešit, přidejte buď možnost příkazového řádku **/analyze** , nebo odeberte neplatné číslo upozornění z příslušné možnosti příkazového řádku **/w** .

## <a name="example"></a>Příklad

Následující příklad příkazového řádku generuje upozornění D9041:

```
cl /EHsc /LD /wd6001 filename.cpp
```

Chcete-li odstranit upozornění, přidejte možnost příkazového řádku **/analyze** . Pokud není **/analyze** ve vaší verzi kompilátoru podporován, odeberte z možnosti **/WD** neplatné číslo upozornění.

## <a name="see-also"></a>Viz také

[Chyby příkazového řádku D8000 až D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Parametry kompilátoru MSVC](../../build/reference/compiler-options.md)
