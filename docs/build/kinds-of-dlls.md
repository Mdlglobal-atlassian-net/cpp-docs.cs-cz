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

Toto téma poskytuje informace, které vám pomůžou určit druh knihovny DLL pro sestavení.

## <a name="different-kinds-of-dlls-available"></a><a name="_core_the_different_kinds_of_dlls_available_with_visual_c.2b2b"></a>K dispozici jsou různé druhy knihoven DLL

Pomocí sady Visual Studio můžete vytvářet knihovny DLL Win32 v jazyce C nebo C++, které nepoužívají knihovnu MFC (Microsoft Foundation Class). Můžete vytvořit projekt non-MFC DLL pomocí Průvodce aplikací Win32.

Knihovna MFC je sama o sobě k dispozici v knihovně statických odkazů nebo v několika knihovnách DLL, a to pomocí Průvodce knihovnou MFC DLL. Pokud vaše knihovna DLL používá knihovnu MFC, Visual Studio podporuje tři různé scénáře vývoje knihovny DLL:

- Sestavení běžné knihovny MFC DLL, která staticky propojuje MFC

- Sestavení běžné knihovny MFC DLL, která dynamicky propojuje MFC

- Sestavení knihovny DLL rozšíření MFC, která vždy dynamicky propojí knihovnu MFC

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Knihovny DLL mimo MFC – přehled](non-mfc-dlls-overview.md)

- [Běžné knihovny MFC DLL staticky propojené s knihovnou MFC](regular-dlls-statically-linked-to-mfc.md)

- [Běžné knihovny MFC DLL dynamicky propojené s knihovnou MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Rozšiřující knihovny MFC DLL: Přehled](extension-dlls-overview.md)

- [Jaký druh knihovny DLL použít](#_core_which_kind_of_dll_to_use)

## <a name="deciding-which-kind-of-dll-to-use"></a><a name="_core_which_kind_of_dll_to_use"></a>Rozhodnutí o tom, jaký druh knihovny DLL použít

Pokud vaše knihovna DLL nepoužívá knihovnu MFC, použijte Visual Studio k sestavení knihovny DLL non-MFC Win32. Propojení vaší knihovny DLL s knihovnou MFC (staticky nebo dynamicky) zabírá významné místo na disku a paměť. Neodkazujte na knihovnu MFC, pokud vaše knihovna DLL skutečně nepoužívá knihovnu MFC.

Pokud vaše knihovna DLL bude používat knihovnu MFC a bude použita v aplikacích MFC nebo non-MFC, je nutné sestavit regulární knihovnu MFC DLL, která dynamicky odkazuje na knihovnu MFC nebo regulární knihovnu MFC DLL, která staticky odkazuje na knihovnu MFC. Ve většině případů pravděpodobně budete chtít použít regulární knihovnu MFC DLL, která dynamicky propojuje ke knihovně MFC, protože velikost souboru knihovny DLL bude mnohem menší a úspory v paměti z použití sdílené verze knihovny MFC mohou být významné. Pokud staticky propojíte s knihovnou MFC, velikost souboru vaší knihovny DLL bude větší a potenciálně zabere dodatečnou paměť, protože načte svou vlastní soukromou kopii kódu knihovny MFC.

Sestavení knihovny DLL, která dynamicky odkazuje na knihovnu MFC je rychlejší než sestavení knihovny DLL, která staticky odkazuje na knihovnu MFC, protože není nutné k samotnému propojení knihovny MFC. To platí zejména v sestavení ladění, kde linker musí komprimovat informace o ladění. Propojením s knihovnou DLL, která již obsahuje ladicí informace, je k dispozici méně ladicích informací pro komprimaci v rámci knihovny DLL.

Jednou nevýhodou pro dynamické propojení s knihovnou MFC je, že je nutné distribuovat sdílené knihovny DLL MFCx0. dll a Msvcrxx. dll (nebo podobné soubory) s vaší knihovnou DLL. Knihovny MFC DLL jsou volně distribuovatelné, ale v instalačním programu je stále nutné nainstalovat knihovny DLL. Kromě toho je nutné dodávat soubor Msvcrxx. dll, který obsahuje běhovou knihovnu jazyka C, která je používána programem i knihovny MFC DLL samotné.

Pokud bude vaše knihovna DLL používána pouze spustitelnými soubory knihovny MFC, můžete si vybrat mezi vytvořením běžné knihovny MFC DLL nebo knihovny DLL rozšíření MFC. Pokud vaše knihovna DLL implementuje opakovaně použitelné třídy odvozené z existujících tříd knihovny MFC nebo potřebujete předat objekty odvozené od knihovny MFC mezi aplikací a knihovnou DLL, je nutné vytvořit rozšiřující knihovnu DLL knihovny MFC.

Pokud vaše knihovna DLL dynamicky odkazuje na knihovnu MFC, knihovny MFC DLL mohou být distribuovány pomocí knihovny DLL. Tato architektura je zvláště užitečná pro sdílení knihovny tříd mezi několika spustitelnými soubory, aby se ušetřilo místo na disku a minimalizovalo využití paměti.

### <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Knihovny DLL mimo MFC – přehled](non-mfc-dlls-overview.md)

- [Běžné knihovny MFC DLL staticky propojené s knihovnou MFC](regular-dlls-statically-linked-to-mfc.md)

- [Běžné knihovny MFC DLL dynamicky propojené s knihovnou MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Rozšiřující knihovny MFC DLL: Přehled](extension-dlls-overview.md)

## <a name="see-also"></a>Viz také

[Vytváření knihoven DLL jazyka C/C++ v aplikaci Visual Studio](dlls-in-visual-cpp.md)
