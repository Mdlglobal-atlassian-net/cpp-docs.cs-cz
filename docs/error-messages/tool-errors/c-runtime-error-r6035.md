---
title: "Chyba v běhu R6035 C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: R6035
dev_langs: C++
helpviewer_keywords: R6035
ms.assetid: f8fb50b8-18bf-4258-b96a-b0a9de468d16
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f0f6e34ef6c95d4c1942cdc1348000213647b0b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-runtime-error-r6035"></a>R6035 Chyba za běhu C
Knihovna prostředí Runtime Microsoft Visual C++, chyba R6035 – Modul této aplikace inicializuje soubor cookie globálního zabezpečení, když se funkce spoléhá na to, že je soubor cookie zabezpečení aktivní.  Call __security_init_cookie earlier.  
  
 [__security_init_cookie –](../../c-runtime-library/reference/security-init-cookie.md) musí být voláno před prvním použitím soubor cookie globálního zabezpečení.  
  
 Soubor cookie globálního zabezpečení se používá k ochraně přetečení vyrovnávací paměti v kódu kompilovat s [/GS (Kontrola zabezpečení vyrovnávací paměti)](../../build/reference/gs-buffer-security-check.md) a kód, který pomocí strukturované zpracování výjimek. Při vstupu do funkce chráněné před přetečením je soubor cookie vložen do zásobníku a při ukončení funkce je hodnota v zásobníku porovnána s globálním souborem cookie. Případný rozdíl mezi nimi značí, že došlo k přetečení vyrovnávací paměti a má za následek okamžité ukončení programu.  
  
 Chyba R6035 značí, že volání `__security_init_cookie` bylo provedeno po vstupu do chráněné funkce. Pokud spuštění pokračuje, mělo by být detekováno falešné přetečení vyrovnávací paměti, protože soubor cookie v zásobníku už neodpovídá globálnímu souboru cookie.  
  
 Podívejte se na následující příklad knihovny DLL. Vstupní bod knihovny DLL je nastavena na DllEntryPoint prostřednictvím linkeru [/Entry (Symbol vstupního bodu)](../../build/reference/entry-entry-point-symbol.md) možnost. Tím se obchází inicializace CRT, která by obvykle inicializovala soubor cookie globálního zabezpečení, takže samotná knihovna DLL musí volat `__security_init_cookie`.  
  
```  
// Wrong way to call __security_init_cookie  
DllEntryPoint(...) {  
   DllInitialize();  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
  
void DllInitialize() {  
   __security_init_cookie();  
}  
```  
  
 Tento příklad vygeneruje chybu R6035, protože vstupní bod DllEntryPoint používá strukturované zpracování výjimek, a proto použije soubor cookie zabezpečení ke zjištění přetečení vyrovnávací paměti. Než se zavolá DllInitialize, soubor cookie globálního zabezpečení je již vložen do zásobníku.  
  
 V tomto příkladu je znázorněn správný způsob:  
  
```  
// Correct way to call __security_init_cookie  
DllEntryPoint(...) {  
   __security_init_cookie();  
   DllEntryHelper();  
}  
  
void DllEntryHelper() {  
   ...  
   __try {  
      ...  
   } __except()... {  
      ...  
   }  
}  
```  
  
 V tomto případě vstupní bod DllEntryPoint není chráněn proti přetečení vyrovnávací paměti (nemá žádné místní vyrovnávací paměti řetězců a nepoužívá strukturované zpracování výjimek), proto může bezpečně volat `__security_init_cookie`. Poté zavolá pomocnou funkci, která je chráněna.  
  
> [!NOTE]
>  Chybová zpráva R6035 se vygeneruje pouze při ladění CRT platformy x86 a pouze pro strukturované zpracování výjimek. Tato podmínka je však chybou na všech platformách a pro všechny formy zpracování výjimek, například zpracování výjimek jazyka C++ EH.  
  
## <a name="see-also"></a>Viz také  
 [Podrobněji kontroly zabezpečení kompilátoru](http://go.microsoft.com/fwlink/?linkid=7260)