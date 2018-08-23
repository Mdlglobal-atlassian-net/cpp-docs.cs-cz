---
title: -kernel (vytvoření jádra binárního režimu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /kernel
- /kernel-
dev_langs:
- C++
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20ea3423acd19a70c5b7b759b9923b0132e04af0
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465654"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (vytvoření binárního režimu jádra)
Vytvoří binární soubor, který lze spustit v jádru Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/kernel[-]  
```  
  
## <a name="arguments"></a>Arguments  
 **/kernel**  
 Kód v aktuálním projektu je zkompilován a propojené s použitím sady pravidel jazyka C++, které jsou specifické pro kód, který se spustí v režimu jádra.  
  
 **/Kernel-**  
 Kód v aktuální projekt je zkompilován a propojené bez použití jazykových pravidel C++, které jsou specifické pro kód, který se spustí v režimu jádra.  
  
## <a name="remarks"></a>Poznámky  
 Neexistuje žádná `#pragma` ekvivalentní pro ovládání této možnosti.  
  
 Zadání **/kernel** přikazuje kompilátoru a linkeru přidělení žádá, které funkce jazyka jsou přípustné v režimu jádra a ujistěte se, že máte dostatek výrazové možnosti, aby modul runtime nestabilitu, který je jedinečný pro v režimu jádra C++. Toho dosahuje tím, že zakazují použití funkcí jazyka C++, které se jedná o narušující v režimu jádra a tím, že poskytuje upozornění funkcí jazyka C++, které jsou potenciálně rušivé, ale nejde zakázat.  
  
 **/Kernel** možnost se vztahuje k jednotlivým fázím kompilátoru a propojovacího programu sestavení a je nastavená na úrovni projektu. Předání **/kernel** přepínač, který určuje kompilátoru, že výsledný binární soubor po propojení, by měly být načteny do jádra Windows. Kompilátor zúží spektru funkcí jazyka C++, který je kompatibilní s rozhraními podmnožině.  
  
 Následující tabulka obsahuje seznam změn v chování kompilátoru při **/kernel** je zadán.  
  
|Typ chování|**/ Kernel** chování|  
|-------------------|---------------------------|  
|Zpracovávání výjimek v jazyce C++|Zakázané. Všechny instance `throw` a `try` chybu kompilátoru generovat klíčová slova (s výjimkou specifikace výjimky `throw()`). Ne **/EH** možnosti jsou kompatibilní s **/kernel**, s výjimkou **/EH-**.|  
|RTTI|Zakázané. Všechny instance `dynamic_cast` a `typeid` klíčová slova generuje chybu kompilátoru, není-li `dynamic_cast` slouží staticky.|  
|`new` a `delete`|Je nutné explicitně definovat `new()` nebo `delete()` operátor; kompilátor ani modul runtime bude zadat výchozí definici.|  
  
 Vlastní konvence volání, [/GS](../../build/reference/gs-buffer-security-check.md) možnost sestavení a všechny optimalizace jsou povolené při použití **/kernel** možnost. Vkládání je do značné míry není ovlivněn **/kernel**, se stejnou sémantikou kompilátorem respektovány. Pokud chcete, abyste měli jistotu, že `__forceinline` vkládání kvalifikátor zachovaný, ujistěte se, že upozornění [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) je povoleno, abyste věděli, když konkrétní `__forceinline` není vložená funkce.  
  
 Pokud je předán kompilátoru **/kernel** přepínače, predefines preprocesorové makro s názvem `_KERNEL_MODE` a hodnotou **1**. Může být využit k podmíněné kompilaci kódu, podle toho, jestli prostředí pro spouštění v uživatelském režimu nebo v režimu jádra. Například následující kód určuje, že třída by měla být v segmentu-stránkované paměti při kompilaci pro spuštění režimu jádra.  
  
```cpp  
#ifdef _KERNEL_MODE  
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))  
#else  
#define NONPAGESECTION  
#endif  
  
class NONPAGESECTION MyNonPagedClass  
{  
   // ...
};  
```  
  
 Některé tyto kombinace Cílová architektura a **/arch** možnost vést k chybě při použití s **/kernel**:  
  
-   **/ arch: {SSE&#124;SSE2&#124;AVX}** x86 se nepodporují. Pouze **/arch:IA32** podporuje **/kernel** na x86.  
  
-   **/ arch: AVX** nepodporuje **/kernel** na x64.  
  
 Sestavování s **/kernel** také předá **/kernel** linkeru. Jí je, jak to ovlivní chování linkeru:  
  
-   Přírůstkové propojování je zakázaná. Pokud chcete přidat **/ incremental** do příkazového řádku, linker generuje tato závažná chyba:  
  
     **LINK: závažná chyba LNK1295: '/ INCREMENTAL' není kompatibilní s "/ jádra" specifikace; propojení bez "/ INCREMENTAL.**  
  
-   Linker zkontroluje každý soubor objektu (nebo žádný člen součástí archivu ze statické knihovny) Chcete-li zobrazit, zda ho může být zkompilovány pomocí **/kernel** možnost ale nebyla. Pokud toto kritérium splňovat všechny instance, linker stále úspěšně propojí, ale může vyvolávat tato upozornění, jak je znázorněno v následující tabulce.  
  
    ||**/ Kernel** obj|**/Kernel-** obj, MASM obj nebo cvtresed|Kombinovat z **/kernel** a **/kernel-** objs|  
    |-|----------------------|-----------------------------------------------|-------------------------------------------------|  
    |**/ Kernel odkaz**|Ano|Ano|Ano, s upozornění LNK4257|  
    |**Odkaz**|Ano|Ano|Ano|  
  
     **LNK4257 objektu nebyl zkompilován s možností/Kernel; bitové kopie se možná nespustí.**  
  
 **/Kernel** možnost a **Driver/Driver** možnost pracovat nezávisle a ani se navzájem ovlivňují.  
  
### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Nastavení možnosti kompilátoru/Kernel v sadě Visual Studio  
  
1.  Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  V **další možnosti** přidejte `/kernel` nebo `/kernel-`.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)