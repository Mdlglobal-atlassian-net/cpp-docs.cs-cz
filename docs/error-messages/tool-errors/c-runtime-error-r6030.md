---
title: Chyba modulu C runtime R6030
ms.date: 11/04/2016
f1_keywords:
- R6030
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
ms.openlocfilehash: 7f5c61d9b39b1d655bcbf3d42ea870370ddf2842
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400016"
---
# <a name="c-runtime-error-r6030"></a>Chyba modulu C runtime R6030

CRT nebyla inicializována

> [!NOTE]
> Pokud k této chybě dojde při spuštění aplikace, aplikace se vypnout, protože má vnitřní problém. Tento problém je nejčastěji způsoben určité softwarové programy zabezpečení, nebo jen zřídka, chyb v programu.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Váš zabezpečovací software může mít konkrétní pokyny pro zmírnění tohoto problému. Zkontrolujte web dodavatele softwaru zabezpečení podrobnosti. Můžete také zkontrolovat aktualizované verze softwaru zabezpečení, nebo vyzkoušejte jinou zabezpečovací software.
> - Použití **aplikace a funkce** nebo **programy a funkce** stránku **ovládací panely** opravte nebo přeinstalujte program.
> - Zkontrolujte **Windows Update** v **ovládací panely** pro aktualizace softwaru.
> - Vyhledat aktualizovanou verzi aplikace. Pokud se problém nevyřeší, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dochází, pokud používáte C Runtime (CRT), ale nebyla spuštěna spouštěcí kód CRT. Je možné se tato chyba, pokud linker [/Entry](../../build/reference/entry-entry-point-symbol.md) k přepsání výchozí počáteční adresu, obvykle se používá **mainCRTStartup**, **wmainCRTStartup** pro konzole EXE, **WinMainCRTStartup** nebo **wWinMainCRTStartup** pro Windows EXE, nebo **_DllMainCRTStartup** pro knihovnu DLL. Pokud jeden z výše uvedené funkce je volána při spuštění, nelze inicializovat modul Runtime jazyka C. Tyto funkce po spuštění jsou obvykle volány ve výchozím nastavení při propojení ke knihovně modulu runtime jazyka C a použít normální **hlavní**, **wmain**, **WinMain**, nebo  **Zpracování funkce DllMain** vstupní body.

Je také možné získat tuto chybu při jiný program využívá i metody pro injektáž kódu na depeše určitých volání knihovny DLL. Tento postup použít některé programy zabezpečení nežádoucí. Ve verzích Visual C++ před Visual Studio 2015 je možné použít k vyřešení příslušného problému staticky propojené knihovny CRT, ale to se nedoporučuje z důvodů aktualizace zabezpečení a aplikace. Oprava tohoto problému může vyžadovat akce koncového uživatele.