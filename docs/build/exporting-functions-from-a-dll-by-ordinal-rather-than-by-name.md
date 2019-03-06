---
title: Export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu
ms.date: 11/04/2016
f1_keywords:
- NONAME
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: fe34ec90aa775e7435d4a02b9d77a9cb9c8fdd65
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423297"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu

Nejjednodušší způsob, jak export funkcí z knihovny DLL je a exportujte je podle názvu. Je to, co se stane, když použijete **__declspec(dllexport)**, např. Ale místo toho můžete exportovat funkce podle řádu. S touto technikou, musíte použít soubor .def místo **__declspec(dllexport)**. K určení funkce pořadové číslo, připojte k názvu funkce v souboru .def jeho pořadové číslo. Informace o zadávání řadové číslovky, naleznete v tématu [export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md).

> [!TIP]
>  Pokud chcete optimalizovat velikost souboru vaše knihovna DLL, použijte **NONAME** atribut u každého exportované funkce. S **NONAME** řadové číslovky atributu, jsou uloženy v knihovně DLL exportovat tabulku, nikoli názvy funkcí. Pokud exportujete mnoho funkcí, to může být značné úspory.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Použijte soubor .def tak můžete exportovat podle pořadových čísel](../build/exporting-from-a-dll-using-def-files.md)

- [Use __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Viz také:

[Export z knihovny DLL](../build/exporting-from-a-dll.md)
