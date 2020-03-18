---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind_bind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4f5b662223914cbb4970188595afb52cc2500cd4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440386"
---
# <a name="allowbind"></a>/ALLOWBIND

Určuje, zda může být vytvořena vazba knihovny DLL.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Poznámky

Možnost **/ALLOWBIND** nastavuje bitovou kopii v hlavičce knihovny DLL, která označuje, že je možné svázat. exe, že bitová kopie může být vázaná. Vazba může způsobit rychlejší načtení obrázku, pokud zavaděč nemusí znovu založit a provést opravu adres pro každou odkazovanou knihovnu DLL. Možná nebudete chtít, aby knihovna DLL byla vázaná, pokud byla digitálně podepsaná – vazba zruší platnost podpisu. Vazba nemá žádný vliv, pokud je pro bitovou kopii povolená náhodnost (ASLR) adresního prostoru pomocí **/DYNAMICBASE** ve verzích Windows, které podporují ASLR.

Použijte **/ALLOWBIND: No** , pokud chcete souboru BIND. exe zabránit v vytvoření vazby knihovny DLL.

Další informace naleznete v tématu [/ALLOWBIND](allowbind-prevent-dll-binding.md) – možnost linkeru.

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](editbin-options.md)
