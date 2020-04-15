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

Nejjednodušší způsob exportu funkcí z dll je exportovat je podle názvu. To se stane, když použijete **__declspec(dllexport)**, například. Místo toho však můžete exportovat funkce podle oslnění. Pomocí této techniky je nutné použít soubor .def namísto **__declspec(dllexport).** Chcete-li určit hodnotu řadového pole, přidejte její řadové číslo k názvu funkce v souboru DEF. Informace o určení řadových čísel naleznete v [tématu Export z dll pomocí souborů .def](exporting-from-a-dll-using-def-files.md).

> [!TIP]
> Chcete-li optimalizovat velikost souboru knihovny DLL, použijte atribut **NONAME** u každé exportované funkce. S atributem **NONAME** jsou ordináty uloženy v tabulce exportu knihovny DLL, nikoli v názvech funkcí. To může být značné úspory, pokud exportujete mnoho funkcí.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Použití souboru DEF, abych mohl exportovat podle řadového](exporting-from-a-dll-using-def-files.md)

- [Použít __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](exporting-from-a-dll.md)
