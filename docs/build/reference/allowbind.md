---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 4cb7e5a3627d865e2f2193dee096c72cced75f5f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819815"
---
# <a name="allowbind"></a>/ALLOWBIND

Určuje, zda může být vázaný knihovny DLL.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Poznámky

**/ALLOWBIND** možnost nastaví bit v hlavičce knihovny DLL, které označuje Bind.exe, že image může být vázána. Vazby lze povolit obrázku, který má načítat rychleji, pokud není zavaděč přenesení změn a provádět opravy adresa pro každý odkazované knihovny DLL. Možná nebudete chtít knihovnu DLL, pokud je digitálně podepsané, vazba zneplatní podpis. Vazba nemá žádný vliv, pokud náhodného generování rozložení prostoru adres (ASLR) je povolený pro bitovou kopii pomocí **možnost/DynamicBase** ve verzích Windows, které podporují technologie ASLR.

Použití **/ALLOWBIND:NO** Bind.exe zabránit vytvoření vazby knihovny DLL.

Další informace najdete v tématu [/ALLOWBIND](allowbind-prevent-dll-binding.md) – možnost linkeru.

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](editbin-options.md)
