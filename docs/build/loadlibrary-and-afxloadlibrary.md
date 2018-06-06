---
title: LoadLibrary a AfxLoadLibrary | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- LoadLibrary
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc3be5d374995c657021952184794f146c37f4dc
ms.sourcegitcommit: d1f576a0f59678edc3d93508cf46485138332178
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753585"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary a AfxLoadLibrary

Zpracovává volání [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187) (nebo [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) explicitně propojit s knihovnou DLL. Pokud funkci úspěšné, mapuje zadané DLL do adresního prostoru volajícího procesu a vrátí popisovač pro knihovnu DLL, kterou lze použít s jinými funkcemi v explicitní propojování – například `GetProcAddress` a `FreeLibrary`.

`LoadLibrary` pokusí se najít knihovnu DLL pomocí stejné pořadí hledání, který se používá pro implicitní propojení. Pokud systém nemůže najít knihovnu DLL nebo pokud vstupní bod funkce vrátí hodnotu FALSE, `LoadLibrary` vrátí hodnotu NULL. Pokud volání `LoadLibrary` Určuje modul knihovny DLL, která je již namapována do adresním prostoru procesu volání funkce vrátí popisovač DLL a zvýší počet odkazů modulu.

Pokud knihovnu DLL má funkci vstupního bodu, operační systém zavolá funkci v kontextu vláken, která volá `LoadLibrary`. Funkce vstupního bodu není volána, pokud knihovnu DLL je již připojen k proces z důvodu předchozích volání `LoadLibrary` má bez odpovídajícího volání `FreeLibrary` funkce.

Pro aplikace MFC, které načítají MFC – rozšiřující knihovny DLL, doporučujeme použít `AfxLoadLibrary` místo `LoadLibrary`. `AfxLoadLibrary` Synchronizace vláken popisovače před voláním `LoadLibrary`. Rozhraní (prototyp funkce) pro `AfxLoadLibrary` je stejný jako `LoadLibrary`.

Pokud systém Windows nemůže načíst knihovnu DLL, můžete proces pokusí o zotavení z chyby. Proces může například upozornit uživatele chyby a požádat uživatele o zadejte jinou cestu ke knihovně DLL.

> [!IMPORTANT]  
> Nezapomeňte zadat úplnou cestu všechny knihovny DLL. Když jsou soubory načteny, prohledají se aktuální adresář nejdřív. Pokud nemáte kvalifikovanou cestu k souboru, soubor, který není zamýšlené může načíst. Chcete-li tomu zabránit jiný způsob je pomocí [/DEPENDENTLOADFLAG](../build/reference/dependentloadflag.md) – možnost linkeru.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Postup propojení implicitně s knihovny DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Rozhodování o způsobu vytváření použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?

- [Pořadí hledání knihoven DLL](https://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)

- [FreeLibrary a AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>Viz také:

- [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)
- [LoadLibrary](https://go.microsoft.com/fwlink/p/?LinkID=259187)
- [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)