---
title: Upozornění příkazového řádku D9041
ms.date: 11/04/2016
f1_keywords:
- D9041
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
ms.openlocfilehash: 2311c61c4d661d58302308f06b08971f94cdacab
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816305"
---
# <a name="command-line-warning-d9041"></a>Upozornění příkazového řádku D9041

Neplatná hodnota 'value' pro '/ možnost'; za předpokladu, že 'value'; Přidat parametr / analyze' pro možnosti příkazového řádku při zadávání tohoto upozornění

Číslo upozornění analýzy kódu byla přidána do **/wd**, **/we**, **/wo**, nebo **/wl** možnost příkazového řádku bez zadání možnosti taky **/ analyze** možnost příkazového řádku. Chcete-li tuto chybu vyřešit, buď přidejte **/ analyze** příkazového řádku, nebo odeberte neplatné číslo upozornění z příslušné **/w** možnost příkazového řádku.

## <a name="example"></a>Příklad

Následující příklad příkazového řádku vygeneruje upozornění D9041:

```
cl /EHsc /LD /wd6001 filename.cpp
```

Chcete-li opravit toto upozornění, přidejte **/ analyze** možnost příkazového řádku. Pokud **/ analyze** se nepodporuje na vaší verzi kompilátoru, odeberte neplatné číslo upozornění z **/wd** možnost.

## <a name="see-also"></a>Viz také

[Chyby příkazového řádku D8000 až D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)<br/>
[Možnosti kompilátoru MSVC](../../build/reference/compiler-options.md)