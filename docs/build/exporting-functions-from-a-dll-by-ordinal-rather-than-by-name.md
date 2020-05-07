---
title: Export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 66e99b18d181e9067e90398c35a61db2da66c301
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328579"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu

Nejjednodušší způsob, jak exportovat funkce z vaší knihovny DLL, je exportovat je podle názvu. K tomu dochází při použití **__declspec (dllexport)**, například. Místo toho ale můžete exportovat funkce podle pořadového čísla. V této technice je nutné použít soubor. def namísto **__declspec (dllexport)**. Chcete-li zadat pořadové číslo funkce, přihlaste své pořadí k názvu funkce v souboru. def. Informace o tom, jak zadat pořadí, naleznete v tématu [Export z knihovny DLL pomocí souborů. def](exporting-from-a-dll-using-def-files.md).

> [!TIP]
> Pokud chcete optimalizovat velikost souboru vaší knihovny DLL, použijte pro každou exportovanou funkci atribut **NONAME** . U atributu **NONAME** jsou řadové číslovky uloženy v exportní tabulce knihovny DLL, nikoli v názvech funkcí. To může být značný úspora, pokud exportujete mnoho funkcí.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Použijte soubor. def, aby se mohl exportovat podle pořadového čísla.](exporting-from-a-dll-using-def-files.md)

- [Použít __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](exporting-from-a-dll.md)
