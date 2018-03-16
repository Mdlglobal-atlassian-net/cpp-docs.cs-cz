---
title: SEGMENT | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- SEGMENT
dev_langs:
- C++
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 253c3b389bd0411e6b5096e914b6a844c8f40805
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="segment"></a>SEGMENT
Definuje segment program volá *název* s atributy segmentu  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### <a name="parameters"></a>Parametry  
 *align*  
 Rozsah adres paměti, ze kterých lze vybrat počáteční adresy segmentu. Typ zarovnání může být jakýkoli z následujících akcí:  
  
|Zarovnat typu|Počáteční adresa|  
|----------------|----------------------|  
|**BYTE**|Další adresa k dispozici bajtů.|  
|**WORD**|Další adresa k dispozici word (2 bajty na slovo).|  
|**DWORD**|Další adresa k dispozici double aplikace word (4 bajty na dvojitou hodnotu word).|  
|**PARA**|Další adresa k dispozici odstavce (16 bajtů za odstavce).|  
|**PAGE**|Další adresa k dispozici stránky (256 bajtů na stránce).|  
|**ALIGN**(*n*)|Další dostupný *n*tý bajtů adresu. Další informace jsou uvedeny v části poznámky.|  
  
 Pokud není tento parametr zadán, **ODSTAVEC** se používá ve výchozím nastavení.  
  
 *kombinování*  
 **VEŘEJNÉ**, **zásobníku**, **běžné**, **paměti**, **v *** adresu*, **PRIVÁTNÍ**  
  
 *Použití*  
 **USE16**, **USE32**, **PLOCHÉ**  
  
 `characteristics`  
 **Informace o**, **ČÍST**, **zápisu**, **EXECUTE**, **SDÍLENÉ**, **NOPAGE**, **NOCACHE**, a **ZAHODIT**  
  
 Tyto jsou podporovány pouze pro COFF a odpovídat vlastností části COFF s podobným názvem (například **SDÍLENÉ** odpovídá IMAGE_SCN_MEM_SHARED). ČTENÍ nastavuje příznak IMAGE_SCN_MEM_READ. Příznak zastaralé jen pro čtení z důvodu části příznaku IMG_SCN_MEM_WRITE. Pokud existuje `characteristics` jsou nastavené, nepoužívají výchozí vlastnosti a jsou platné pouze příznaky programátory zadaný.  
  
 `ALIAS(` `string` `)`  
 Tento řetězec se používá jako název oddílu v emitovaného COFF objektu.  Vytvoří se stejným názvem externí, s odlišné názvy segment MASM více oddílů.  
  
 Není podporováno s **/omf**.  
  
 `class`  
 Určuje, jak by měla být segmenty kombinaci a řazení v sestavený souboru. Jsou typické hodnoty, `'DATA'`, `'CODE'`, `'CONST'` a `'STACK'`  
  
## <a name="remarks"></a>Poznámky  
 Pro `ALIGN(n)`, `n` může být jakékoli power 2 od 1 do 8192; není podporován s **/omf**.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)