---
title: Chyba modulu C runtime R6030
ms.date: 11/04/2016
f1_keywords:
- R6030
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
ms.openlocfilehash: 5d7160623d4e1eb83240c09e637c780fefc0d43d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197116"
---
# <a name="c-runtime-error-r6030"></a>Chyba modulu C runtime R6030

CRT Neinicializováno

> [!NOTE]
> Pokud se zobrazí tato chybová zpráva při spuštění aplikace, aplikace byla vypnuta, protože došlo k vnitřnímu problému. Tento problém je nejčastěji způsoben některými softwarovými programy zabezpečení nebo zřídka pomocí chyby v programu.
>
> Zkuste chybu odstranit pomocí tohoto postupu:
>
> - Bezpečnostní software může mít konkrétní pokyny pro zmírnění tohoto problému. Podrobnosti najdete na webu dodavatele bezpečnostního softwaru. Případně můžete vyhledat aktualizované verze softwaru zabezpečení nebo vyzkoušet jiný bezpečnostní software.
> - K opravě nebo přeinstalaci programu použijte stránku **aplikace a funkce** nebo **programy a funkce** v **Ovládacích panelech** .
> - Ověřte **web Windows Update** v **Ovládacích panelech** pro aktualizace softwaru.
> - Vyhledejte aktualizovanou verzi aplikace. Pokud potíže potrvají, obraťte se na dodavatele aplikace.

**Informace pro programátory**

K této chybě dochází, pokud používáte modul runtime jazyka C (CRT), ale spouštěcí kód CRT nebyl proveden. Tato chyba se může zobrazit v případě, že přepínač linkeru [/entry](../../build/reference/entry-entry-point-symbol.md) slouží k přepsání výchozí počáteční adresy, obvykle **mainCRTStartup**, **wmainCRTStartup** pro konzolový exe, **WinMainCRTStartup** nebo **wWinMainCRTStartup** pro program exe systému Windows nebo **_DllMainCRTStartup** pro knihovnu DLL. Pokud se při spuštění nevolá jedna z výše uvedených funkcí, modul runtime jazyka C se neinicializuje. Tyto spouštěcí funkce jsou obvykle volány ve výchozím nastavení, když propojíte knihovnu prostředí runtime jazyka C a použijete **normální vstupní**body, **wmain**, **WinMain**nebo **DllMain** .

Tato chyba je také možné získat, pokud jiný program používá techniky vkládání kódu k zachycení některých volání knihoven DLL. Tento postup používají některé rušivé bezpečnostní programy. Ve verzích vizuálu C++ před visual Studio 2015 je možné použít staticky propojenou knihovnu CRT k vyřešení problému, ale nedoporučuje se z důvodů aktualizací zabezpečení a aplikací. Oprava tohoto problému může vyžadovat akci koncového uživatele.
