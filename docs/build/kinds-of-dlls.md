---
title: Druhy knihoven DLL
ms.date: 11/04/2016
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: f4aa8b1be7cd9ad32b10f12c5d1dfd3ae86adc1d
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341778"
---
# <a name="kinds-of-dlls"></a>Druhy knihoven DLL

Toto téma obsahuje informace, které vám pomohou určit druh Knihovny k sestavení.

##  <a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a> Různé typy dostupných knihoven DLL

Visual C++ můžete sestavit Win32 knihovny DLL v jazyce C nebo C++, které nepoužívají knihovny Microsoft Foundation Class (MFC). Vytvořte projekt knihovny MFC DLL pomocí Průvodce aplikací Win32.

Samotné knihovny MFC je k dispozici ve statickém propojení knihoven nebo v řadě knihoven DLL s průvodcem knihovny MFC DLL. Pokud vaše knihovna DLL používána knihovnou MFC, Visual C++ podporuje tři různé scénáře vývoje knihovny DLL:

- Sestavování běžné knihovny MFC DLL, která staticky propojuje knihovnu MFC

- Sestavování běžné knihovny MFC DLL, která dynamicky propojuje knihovnu MFC

- Sestavování rozšiřující knihovny DLL MFC, která vždy dynamicky propojí knihovnu MFC

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Knihovny DLL mimo MFC: Přehled](non-mfc-dlls-overview.md)

- [Regulární knihovny MFC DLL staticky propojené do MFC](regular-dlls-statically-linked-to-mfc.md)

- [Regulární knihovny MFC DLL staticky propojené do MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Rozšiřující knihovny MFC DLL: Přehled](extension-dlls-overview.md)

- [Jaký druh knihovny DLL použít](#_core_which_kind_of_dll_to_use)

##  <a name="_core_which_kind_of_dll_to_use"></a> Rozhodování o tom, jaký druh knihovny DLL použít

Pokud vaše knihovna DLL nepoužívá knihovnu MFC, použijte Visual C++ k sestavení non - MFC Win32 DLL. Propojování vaší knihovny DLL ke knihovně MFC (staticky nebo dynamicky) zabere značnou část disku a paměti. Neměli byste propojovat ke knihovně MFC, pokud vaše knihovna DLL aktuálně nepoužívá knihovnu MFC.

Pokud vaše knihovna DLL používat knihovnu MFC a budou používat aplikace knihovny MFC nebo knihovny non-MFC, musíte sestavit obvyklou knihovnu DLL MFC, která dynamicky propojuje ke knihovně MFC nebo běžné knihovny MFC DLL, která staticky propojuje ke knihovně MFC. Ve většině případů budete pravděpodobně chtít použít běžné knihovny MFC DLL dynamicky propojuje ke knihovně MFC, protože velikost souboru knihovny DLL bude mnohem menší a mohou být Úspora paměti narozdíl od použití sdílených verzí knihovny MFC. Pokud staticky propojíte ke knihovně MFC, velikost souboru knihovny DLL bude větší a potenciálně zabere dodatečnou paměť, protože je načtena vlastní soukromá kopie kódu knihovny MFC.

Sestavení knihovny DLL, která dynamicky propojuje ke knihovně MFC je rychlejší než sestavování knihovny DLL, která staticky propojuje ke knihovně MFC, protože není nutné samostatně propojit knihovnu MFC. To platí zejména v sestavení ladění, kde musí propojovací program kompaktně ladit informace. Díky propojení s knihovnou DLL, která už obsahuje informace o ladění, je méně ladících informací ke spojení v rámci vaší DLL Knihovny.

Jednou nevýhodou dynamického propojení ke knihovně MFC je, že musíte distribuovat sdílené knihovny DLL Mfcx0.dll a Msvcrxx.dll (nebo podobné soubory) s vaší knihovou DLL. Knihovny DLL MFC jsou volně redistribuovány, ale stále je nutné nainstalovat knihovny DLL ve vašem instalačním programu. Kromě toho můžete musíte poskytnout Msvcrxx.dll, která obsahuje knihovny runtime jazyka C, který se používá i tak, že váš program a samotnými knihovnami MFC DLL.

Pokud vaše knihovna DLL bude použita pouze spustitelnými soubory knihovny MFC, máte možnost volby mezi sestavením běžné knihovny MFC DLL nebo rozšiřující knihovny DLL MFC. Pokud vaše knihovna DLL opakovaně implementuje použitelné třídy odvozené z existujících tříd knihovny MFC nebo potřebujete předat mezi aplikací a knihovny DLL MFC odvozené objekty, musíte sestavit rozšiřující knihovny DLL MFC.

Pokud vaše knihovna DLL dynamicky propojuje ke knihovně MFC, knihovny DLL MFC můžou být znovu distribuovány s vaší knihovou DLL. Tato architektura je zvláště užitečná pro sdílení knihovny tříd mezi několika spustitelnými soubory k ušetřit místo na disku a minimalizuje využití paměti.

Před verzí 4.0 podporují Visual C++ pouze dva druhy knihoven DLL, které používají knihovnu MFC: USRDLL a AFXDLL. Regulární knihovny MFC DLL staticky propojené do MFC mají stejné vlastnosti jako dosavadní USRDLL. Rozšiřující knihovny DLL MFC mají stejné vlastnosti jako dřívější AFXDLL.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Knihovny DLL mimo MFC: Přehled](non-mfc-dlls-overview.md)

- [Regulární knihovny MFC DLL staticky propojené do MFC](regular-dlls-statically-linked-to-mfc.md)

- [Regulární knihovny MFC DLL staticky propojené do MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Rozšiřující knihovny MFC DLL: Přehled](extension-dlls-overview.md)

## <a name="see-also"></a>Viz také:

[Knihovny DLL v jazyce Visual C++](dlls-in-visual-cpp.md)
