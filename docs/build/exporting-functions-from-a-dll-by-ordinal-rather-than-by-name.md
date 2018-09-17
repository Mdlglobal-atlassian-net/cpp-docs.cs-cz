---
title: Export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- NONAME
dev_langs:
- C++
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d894df971dd0c50556a420eafa2909474ee6912
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714256"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu

Nejjednodušší způsob, jak export funkcí z knihovny DLL je a exportujte je podle názvu. Je to, co se stane, když použijete **__declspec(dllexport)**, např. Ale místo toho můžete exportovat funkce podle řádu. S touto technikou, musíte použít soubor .def místo **__declspec(dllexport)**. K určení funkce pořadové číslo, připojte k názvu funkce v souboru .def jeho pořadové číslo. Informace o zadávání řadové číslovky, naleznete v tématu [export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md).

> [!TIP]
>  Pokud chcete optimalizovat velikost souboru vaše knihovna DLL, použijte **NONAME** atribut u každého exportované funkce. S **NONAME** řadové číslovky atributu, jsou uloženy v knihovně DLL exportovat tabulku, nikoli názvy funkcí. Pokud exportujete mnoho funkcí, to může být značné úspory.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Použijte soubor .def tak můžete exportovat podle pořadových čísel](../build/exporting-from-a-dll-using-def-files.md)

- [Pomocí deklarace __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](../build/exporting-from-a-dll.md)