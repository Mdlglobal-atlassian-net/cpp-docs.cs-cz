---
title: Podpora národních prostředí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5afb7bd027fca215e1c10c111132ee881ad49548
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018062"
---
# <a name="international-enabling"></a>Podpora národních prostředí
Většina tradičních kód jazyka C a C++ díky předpoklady o znaků a práci s řetězci, které fungují dobře u mezinárodní aplikace. Zatímco knihovny MFC a knihovny run-time podporují kódování Unicode a MBCS, je stále pracovní musíte udělat. A provede vás, tato část vysvětluje význam "podpora národních prostředí" v jazyce Visual C++:  
  
-   Kódování Unicode a MBCS jsou povolené pomocí přenosné datové typy v seznamech parametrů funkce MFC a návratové typy. Tyto typy jsou definovány podmíněně vhodné způsoby v závislosti na tom, zda vaše sestavení definuje symbol `_UNICODE` nebo symbol `_MBCS` (což znamená, že DBCS). Různé varianty knihovny MFC jsou automaticky propojeny s vaší aplikací, v závislosti na tom, které tyto dva symboly definuje sestavení.  
  
-   Kód knihovny třídy používá k zajištění správného chování v kódování Unicode a MBCS přenosné funkce za běhu a jiným způsobem.  
  
-   Stále musí zpracovávat určité druhy úloh internacionalizace ve vašem kódu:  
  
    -   Použijte stejné přenosná běhové funkce, které usnadňují přenositelných pod buď prostředí MFC.  
  
    -   Vytvořte řetězcové literály a znaky přenositelných pod buď prostředí pomocí `_T` – makro. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
    -   Při analýze řetězce v rámci znakové sady MBCS opatření. Tato opatření nejsou potřebné v kódování Unicode. Další informace najdete v tématu [MBCS – tipy pro programování](../text/mbcs-programming-tips.md).  
  
    -   Zajistíme, jsou-li zkombinovány ANSI (8 bitů) a znaky kódování Unicode (16-bit) ve vaší aplikaci. Je možné použít znaky ANSI v některé části programu a znaky kódování Unicode v jiné, ale není možné kombinovat do jednoho řetězce.  
  
    -   To není pevně zakódované řetězce ve vaší aplikaci. Místo toho proveďte jejich prostředky STRINGTABLE jejich přidáním do souboru .rc aplikace. Vaše aplikace může být lokalizována bez nutnosti změny zdrojového kódu nebo opětovnou kompilaci. Další informace o prostředcích STRINGTABLE najdete v tématu [Editor řetězců](../windows/string-editor.md).  
  
> [!NOTE]
>  Znakové sady MBCS a Evropský mají některé znaky, jako je například písmena s diakritikou, s větší než 0x80 kódy znaků. Vzhledem k tomu, že většinu kódu používá podepsané znaky, tyto znaky, které jsou větší než 0x80 se rozšířen o znaménko při převodu na **int**. Jedná o problém pro indexování pole, protože rozšířen o znaménko znaky, je záporná, indexy mimo pole. Jazyky, které používají znakovou sadu MBCS, jako je například japonštinu, jsou také jedinečné. Protože znak může sestávat z 1 nebo 2 bajty, by měla vždy pracovat oba bajtů ve stejnou dobu.  
  
## <a name="see-also"></a>Viz také  
 [Kódování Unicode a MBCS](../text/unicode-and-mbcs.md)   
 [Strategie internacionalizace](../text/internationalization-strategies.md)