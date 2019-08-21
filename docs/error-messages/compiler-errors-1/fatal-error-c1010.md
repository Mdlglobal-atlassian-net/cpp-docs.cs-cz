---
title: Závažná chyba C1010
ms.date: 08/19/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 35b0f60f7eb3be887598e7ffaf3e3eae74aefcff
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630784"
---
# <a name="fatal-error-c1010"></a>Závažná chyba C1010

při hledání předkompilované hlavičky byl zjištěn neočekávaný konec souboru. Nezapomněli jste do zdroje přidat název #include?

Soubor zahrnutí zadaný pomocí [/Yu](../../build/reference/yu-use-precompiled-header-file.md) není uveden ve zdrojovém souboru.  Tato možnost je ve výchozím nastavení povolená ve většině C++ typů projektů sady Visual Studio a souboru *PCH. h* (*stdafx. h* v aplikaci Visual Studio 2017 a starší) je výchozím souborem zahrnutí zadaným pomocí této možnosti.

V prostředí sady Visual Studio použijte k vyřešení této chyby jednu z následujících metod:

- Pokud ve svém projektu nepoužíváte předkompilované hlavičky, nastavte vlastnost **vytvořit/použít předkompilované záhlaví** zdrojových souborů na nepoužívají **předkompilované hlavičky**. K nastavení této možnosti kompilátoru použijte následující postup:

   1. V podokně Průzkumník řešení projektu klikněte pravým tlačítkem myši na název projektu a potom klikněte na příkaz **vlastnosti**.

   1. V levém podokně klikněte na složku **C/C++**  .

   1. Klikněte na uzel **předkompilované hlavičky** .

   1. V pravém podokně klikněte na **vytvořit/použít předkompilovanou hlavičku**a pak klikněte na nepoužívat **předkompilované hlavičky**.

- Ujistěte se, že jste neúmyslně odstranili, přejmenovali nebo odebrali hlavičkový soubor (ve výchozím nastavení stdafx. h) z aktuálního projektu. Tento soubor musí být také zahrnut před jakýmkoli jiným kódem ve zdrojových souborech pomocí **#include stdafx. h**. (Tento hlavičkový soubor je zadaný jako vlastnost souborového projektu **vytvořit/použít PCH** .)