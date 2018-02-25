---
title: "část | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- section_CPP
- vc-pragma.section
dev_langs:
- C++
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 10f5783c6712852bfb53f457cea174f699c01ea0
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="section"></a>section
Vytvoří oddíl v souboru .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma section( "section-name" [, attributes] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Význam podmínky *segment* a *části* se zaměňovat v tomto tématu.  
  
 Jakmile je definována část, zůstává platná pro zbytek kompilace. Ale musí používat [__declspec(allocate)](../cpp/allocate.md) nebo nic budou umístěny v oddílu.  
  
 *Název oddílu* je povinný parametr, který bude mít název oddílu. Název nesmí být v konfliktu s názvy standardní části. V tématu [/SECTION](../build/reference/section-specify-section-attributes.md) pro seznam názvů byste neměli používat při vytváření oddílu.  
  
 `attributes` je volitelný parametr, který se skládá z jedné nebo více oddělených čárkami atributy, které chcete přiřadit k části. Možné `attributes` jsou:  
  
 **read**  
 Umožňuje operací čtení na data.  
  
 **write**  
 Umožňuje operací zápisu na data.  
  
 **Spuštění**  
 Umožňuje spuštění.  
  
 **shared**  
 Sdílí části mezi všechny procesy, které načíst obrázek.  
  
 **nopage**  
 Označí části jako stránkovatelné; Tato možnost je užitečná pro ovladače zařízení Win32.  
  
 **nocache**  
 Označí části jako Uložitelný; Tato možnost je užitečná pro ovladače zařízení Win32.  
  
 **Zahodit**  
 Označí části jako discardable; Tato možnost je užitečná pro ovladače zařízení Win32.  
  
 **remove**  
 Označí části jako není rezidentní; virtuální ovladače zařízení (V*x*D) jenom.  
  
 Pokud nezadáte atributy, v části bude mít pro čtení a zápis atributů.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu identifikuje první instrukcí v části a jeho atributy. Celé číslo `j` není uveden do `mysec` vzhledem k tomu, že nebyl deklarován s `__declspec(allocate)`; `j` přejde do datové části. Celé číslo `i` přejděte do `mysec` na základě těchto jeho `__declspec(allocate)` atribut třídy úložiště.  
  
```  
// pragma_section.cpp  
#pragma section("mysec",read,write)  
int j = 0;  
  
__declspec(allocate("mysec"))  
int i = 0;  
  
int main(){}  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)