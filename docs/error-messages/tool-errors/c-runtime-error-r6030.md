---
title: Chyba modulu Runtime jazyka C za r6030 jazyka | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6030
dev_langs:
- C++
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d25969a9ecb833c53b93135e65fa27b4f005a0d
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861197"
---
# <a name="c-runtime-error-r6030"></a>Chyba modulu Runtime jazyka C za r6030 jazyka

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