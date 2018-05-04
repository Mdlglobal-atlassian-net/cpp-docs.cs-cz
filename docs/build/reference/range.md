---
title: -ROZSAHU | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d06d699500ba3ea441af61a2e2a5a0da3f96903a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="range"></a>/RANGE
Upravuje výstup dumpbin při použití s jinými možnostmi dumpbin, jako je například /RAWDATA nebo /DISASM.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/RANGE:vaMin[,vaMax]  
```  
  
## <a name="flags"></a>Příznaky  
 **vaMin**  
 Virtuální adresa, kdy chcete operaci dumpbin zahájíte.  
  
 **vaMax** (volitelné)  
 Virtuální adresa, kdy chcete dumpbin operaci ukončete. Pokud není zadáno, bude dumpbin přejděte na konec souboru.  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete zobrazit virtuální adresy pro bitovou kopii, použijte pro bitovou kopii (RVA + základní), souboru s mapováním **/DISASM** nebo **/HEADERS** – možnost nástroje dumpbin nebo okno zpětný překlad v ladicím programu sady Visual Studio.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu **/rozsahu** slouží k úpravě zobrazení **/disasm** možnost. V tomto příkladu výchozí hodnota je vyjádřena jako s desetinným číslem a koncová hodnota je zadán jako hexadecimální číslo.  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## <a name="see-also"></a>Viz také  
 [DUMPBIN – možnosti](../../build/reference/dumpbin-options.md)