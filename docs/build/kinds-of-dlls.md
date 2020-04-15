---
title: Druhy knihoven DLL
ms.date: 05/06/2019
helpviewer_keywords:
- MFC DLLs [C++], types
- DLLs [C++], types
- DLLs [C++], MFC
ms.assetid: f6a30db9-6138-4b2c-90cc-a17855e499a6
ms.openlocfilehash: dae44d2dd39597420ce2a2c4e1642e8a7f0784e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328504"
---
# <a name="kinds-of-dlls"></a>Druhy knihoven DLL

Toto téma obsahuje informace, které vám pomohou určit druh dll sestavení.

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>K dispozici jsou různé druhy knihoven DLL

Pomocí sady Visual Studio můžete vytvářet knihovny DLL Win32 v jazyce C nebo C++, které nepoužívají knihovnu třídy Microsoft Foundation (MFC). Pomocí Průvodce aplikací win32 můžete vytvořit projekt knihovny DLL bez knihovny MFC.

Samotná knihovna knihovny Knihovny MFC je k dispozici v knihovnách statických odkazů nebo v několika knihovnách DLL pomocí Průvodce knihovnou DLL knihovny MFC. Pokud knihovna DLL používá knihovnu MFC, visual studio podporuje tři různé scénáře vývoje knihovny DLL:

- Vytváření běžné knihovny DLL knihovny MFC, která staticky propojuje knihovnu MFC

- Vytváření běžné knihovny DLL knihovny MFC, která dynamicky propojuje knihovnu MFC

- Vytváření knihovny DLL rozšíření knihovny MFC, která vždy dynamicky propojuje knihovnu MFC

### <a name="what-do-you-want-to-know-more-about"></a>O čem chcete vědět více?

- [Knihovny DLL mimo MFC – přehled](non-mfc-dlls-overview.md)

- [Běžné knihovny DLL knihovny MFC staticky propojené s knihovnou MFC](regular-dlls-statically-linked-to-mfc.md)

- [Běžné knihovny DLL knihovny MFC dynamicky propojené s knihovnou MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Rozšiřující knihovny MFC DLL: Přehled](extension-dlls-overview.md)

- [Jaký druh dll použít](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>Rozhodování o tom, jaký druh dll použít

Pokud knihovna DLL nepoužívá knihovnu MFC, použijte visual studio k vytvoření knihovny DLL bez knihovny MFC Win32. Propojení knihovny DLL s knihovnou MFC (staticky nebo dynamicky) zabírá značné místo na disku a paměť. Neměli byste odkazovat na knihovnu MFC, pokud knihovna DLL skutečně nepoužívá knihovnu MFC.

Pokud vaše knihovna DLL bude používat knihovnu MFC a bude používána aplikacemi knihovny MFC nebo jiné ho fc, musíte vytvořit buď běžnou knihovnu MFC DLL, která dynamicky odkazuje na knihovnu MFC, nebo běžnou knihovnu DLL knihovny MFC, která staticky odkazuje na knihovnu MFC. Ve většině případů pravděpodobně budete chtít použít pravidelnou knihovnu DLL knihovny MFC, která dynamicky odkazuje na knihovnu MFC, protože velikost souboru knihovny DLL bude mnohem menší a úspory paměti z použití sdílené verze knihovny MFC mohou být významné. Pokud staticky odkazujete na knihovnu MFC, velikost souboru knihovny DLL bude větší a potenciálně zabere další paměť, protože načte vlastní soukromou kopii kódu knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny knihovny.

Vytváření knihovny DLL, která dynamicky odkazuje na knihovnu MFC, je rychlejší než vytváření knihovny DLL, která staticky odkazuje na knihovnu MFC, protože není nutné propojit samotnou knihovnu MFC. To platí zejména v sestavení ladění, kde propojovací systém musí komprimovat informace o ladění. Propojením s dll, která již obsahuje informace o ladění, je méně ladicí informace k komprimaci v rámci dll.

Jednou z nevýhod dynamického propojení s knihovnou MFC je, že je nutné distribuovat sdílené knihovny DLL Mfcx0.dll a Msvcrxx.dll (nebo podobné soubory) s knihovnou DLL. Knihovny DLL knihovny MFC jsou volně redistribuovatelné, ale stále je nutné nainstalovat knihovny DLL v instalačním programu. Kromě toho je nutné dodat knihovnu Msvcrxx.dll, která obsahuje knihovnu c run-time, která je používána programem i samotnými knihovnami DLL knihovny MFC.

Pokud vaše knihovna DLL bude používána pouze spustitelnými soubory knihovny MFC, máte na výběr mezi vytvořením běžné knihovny DLL knihovny MFC nebo rozšiřující knihovny DLL knihovny MFC. Pokud knihovna DLL implementuje opakovaně použitelné třídy odvozené z existujících tříd knihovny MFC nebo potřebujete předat objekty odvozené knihovnou MFC mezi aplikací a knihovnou DLL, musíte vytvořit knihovnu DLL rozšíření knihovny MFC.

Pokud knihovna DLL dynamicky odkazuje na knihovnu MFC, mohou být knihovny DLL knihovny MFC dále distribuovány spolu s knihovnou DLL. Tato architektura je zvláště užitečná pro sdílení knihovny tříd mezi více spustitelnými soubory, čímž šetří místo na disku a minimalizuje využití paměti.

### <a name="what-do-you-want-to-know-more-about"></a>O čem chcete vědět více?

- [Knihovny DLL mimo MFC – přehled](non-mfc-dlls-overview.md)

- [Běžné knihovny DLL knihovny MFC staticky propojené s knihovnou MFC](regular-dlls-statically-linked-to-mfc.md)

- [Běžné knihovny DLL knihovny MFC dynamicky propojené s knihovnou MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Rozšiřující knihovny MFC DLL: Přehled](extension-dlls-overview.md)

## <a name="see-also"></a>Viz také

[Vytvoření knihoven DLL c/C++ v sadě Visual Studio](dlls-in-visual-cpp.md)
