---
title: -ALLOWBIND | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ce0a33ebb0b8b9ba34ac241c8335e9524dec08b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715569"
---
# <a name="allowbind"></a>/ALLOWBIND

Určuje, zda může být vázaný knihovny DLL.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Poznámky

**/ALLOWBIND** možnost nastaví bit v hlavičce knihovny DLL, které označuje Bind.exe, že image může být vázána. Vazby lze povolit obrázku, který má načítat rychleji, pokud není zavaděč přenesení změn a provádět opravy adresa pro každý odkazované knihovny DLL. Možná nebudete chtít knihovnu DLL, pokud je digitálně podepsané, vazba zneplatní podpis. Vazba nemá žádný vliv, pokud náhodného generování rozložení prostoru adres (ASLR) je povolený pro bitovou kopii pomocí **možnost/DynamicBase** ve verzích Windows, které podporují technologie ASLR.

Použití **/ALLOWBIND:NO** Bind.exe zabránit vytvoření vazby knihovny DLL.

Další informace najdete v tématu [/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md) – možnost linkeru.

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](../../build/reference/editbin-options.md)