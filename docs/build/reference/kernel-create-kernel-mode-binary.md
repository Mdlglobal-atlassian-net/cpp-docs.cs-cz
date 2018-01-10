---
title: "-kernel (vytvoření jádra režimu Binary) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /kernel
- /kernel-
dev_langs: C++
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0e20df59788577acb680cbd18b737f7ec2d7822
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel (vytvoření binárního režimu jádra)
Vytvoří binární soubor, který lze spustit v jádru systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/kernel[-]  
```  
  
## <a name="arguments"></a>Arguments  
 **/ Kernel**  
 Kód v aktuálním projektu je zkompilovat a propojit pomocí sadu pravidel jazyka C++, které jsou specifické pro kód, který se spustí v režimu jádra.  
  
 **/Kernel-**  
 Kód v aktuálním projektu je zkompilovat a propojit bez použití pravidla jazyka C++, které jsou specifické pro kód, který se spustí v režimu jádra.  
  
## <a name="remarks"></a>Poznámky  
 Neexistuje žádné `#pragma` ekvivalentní k řízení tuto možnost.  
  
 Určení **/kernel** informuje – možnost kompilátoru a linkeru přidělení žádá funkce jazyka, které jsou přípustné v režimu jádra a ujistěte se, že, zda máte dostatečná výrazovou sílu, aby se zabránilo nestabilitě runtime, který je jedinečné pro C++ v režimu jádra. To lze provést používání funkcí jazyka C++, které jsou v režimu jádra rušivým zásahům a tím, že poskytuje upozornění funkcí jazyka C++, které jsou potenciálně nebezpečné, ale nelze zakázat.  
  
 **/Kernel** možnost se vztahuje na kompilátoru a linkeru fáze sestavení a je nastavená na úrovni projektu. Předat **/kernel** přepínače kompilátoru indikující, že výsledný binární soubor po propojení, by měla být načtena do jádra systému Windows. Kompilátor zúží spektrum funkcí jazyka C++ na určitou podskupinu, který je kompatibilní s jádrem.  
  
 Následující tabulka uvádí změny v chování kompilátoru při **/kernel** je zadán.  
  
|Typ chování|**/ Kernel** chování|  
|-------------------|---------------------------|  
|Zpracovávání výjimek v jazyce C++|Zakázané. Všechny instance `throw` a `try` Chyba kompilátoru emitování klíčová slova (s výjimkou specifikace výjimek `throw()`). Ne **/EH** možnosti jsou kompatibilní s **/kernel**, s výjimkou **/EH-**.|  
|RTTI|Zakázané. Všechny instance `dynamic_cast` a `typeid` klíčová slova emitování kompilátoru chybu, pokud `dynamic_cast` slouží staticky.|  
|`new`a`delete`|Je nutné explicitně zadat `new()` nebo `delete()` operátor; kompilátor ani modulu runtime bude zadat výchozí definici.|  
  
 Vlastní konvence, volání [/GS](../../build/reference/gs-buffer-security-check.md) možnost sestavení a všechny optimalizace, které jsou povoleny při použití **/kernel** možnost. Vložené je z velké části není vliv **/kernel**, se stejnou sémantiku berou v úvahu kompilátoru. Pokud chcete Ujistěte se, že `__forceinline` vložené kvalifikátor je dodržení, ujistěte se, že upozornění [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) je povoleno, abyste věděli, když konkrétní `__forceinline` není vložená funkce.  
  
 Pokud je předán do kompilátoru **/kernel** přepínače, predefines makro preprocesoru, který je pojmenován `_KERNEL_MODE` a má hodnotu **1**. To vám pomůže Podmíněná kompilace kódu na základě toho, jestli prostředí pro spuštění v uživatelském režimu nebo v režimu jádra. Například následující kód určuje, zda by třída segment nestránkovatelné paměti při kompilaci pro spuštění režimu jádra.  
  
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
  
 Některé tyto kombinace cílové architektury a **/arch** možnost vytvořit chybu, pokud se používá s **/kernel**:  
  
-   **/ arch: {SSE &#124; SSE2 &#124; AVX}** na x86 nejsou podporované. Pouze **/arch:IA32** je podporovaná s **/kernel** na x86.  
  
-   **/arch:AVX** není podporovaný s **/kernel** na x64.  
  
 Sestavování s použitím **/kernel** také předá **/kernel** linkeru. Jí je, jak to ovlivňuje linkeru chování:  
  
-   Přírůstkové propojování je zakázána. Pokud přidáte **/ přírůstkové** na příkazový řádek linkeru vysílá Tato závažná chyba:  
  
     **ODKAZ: závažná chyba LNK1295: '/ PŘÍRŮSTKOVÉ' není kompatibilní s ' / jádra, specifikace; propojení bez '/ PŘÍRŮSTKOVÉ'**  
  
-   Linkeru zkontroluje každý objekt soubor (nebo kteréhokoli člena součástí archivu ze statické knihovny) zobrazte, zda se může sestavili jsme pomocí **/kernel** možnost ale nebyla. Pokud všechny instance splňují toto kritérium, linkeru stále úspěšně odkazy, ale může vydat varování, jak je znázorněno v následující tabulce.  
  
    ||**/ Kernel** obj.|**/Kernel-** obj MASM obj nebo cvtresed|Kombinovat z **/kernel** a **/kernel-** objs|  
    |-|----------------------|-----------------------------------------------|-------------------------------------------------|  
    |**/ Kernel odkaz**|Ano|Ano|Ano s upozorněním LNK4257|  
    |**odkaz**|Ano|Ano|Ano|  
  
     **LNK4257 spojujícího objektu není kompilovat s/kernel; bitová kopie nemusí fungovat.**  
  
 **/Kernel** možnost a **/Driver** možnost pracovat nezávisle a ani jeden z nich má vliv na druhý.  
  
### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Nastavení možnosti kompilátoru/Kernel v sadě Visual Studio  
  
1.  Otevřete **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **C/C++** složky.  
  
3.  Vyberte **příkazového řádku** stránku vlastností.  
  
4.  V **další možnosti** přidejte `/kernel` nebo `/kernel-`.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)