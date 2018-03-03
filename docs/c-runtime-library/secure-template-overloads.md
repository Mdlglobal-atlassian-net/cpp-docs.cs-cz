---
title: "Přetížení zabezpečení šablony | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
dev_langs:
- C++
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92ad08738ea2c8c748ac642c5ea15f4b0a257da9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="secure-template-overloads"></a>Přetížení zabezpečení šablony
Microsoft má zastaralé mnoho C Runtime (CRT) – funkce knihovny považuje verze zdokonaleným zabezpečením. Například `strcpy_s` je bezpečnější náhradou `strcpy`. Zastaralé funkce jsou běžné zdroje chyb zabezpečení, protože nebrání operace, které můžete přepsat paměti. Ve výchozím nastavení vyvolá kompilátor vyřazení upozornění, když použijete jednu z těchto funkcí. CRT poskytuje C++ šabloně přetížení pro tyto funkce, které umožňují snadný přechod bezpečnější variant.  
  
Například tento fragment kódu generuje upozornění, protože `strcpy` je zastaralý:  
  
```cpp  
char szBuf[10];  
strcpy(szBuf, "test"); // warning: deprecated  
```
  
Upozornění na zastarání existuje říct, že váš kód může nebezpečný. Pokud jste ověřili, že váš kód nelze přepsat paměti, máte několik možností. Můžete ignorovat upozornění, můžete definovat symbol `_CRT_SECURE_NO_WARNINGS` před příkazy include pro CRT hlavičky k potlačení upozornění, nebo můžete aktualizovat kód pro použití `strcpy_s`:  
  
```cpp  
char szBuf[10];  
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function  
```
  
Přetížení šablony poskytují další možnosti. Pokud definujete `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` hodnotu 1, to umožňuje šabloně přetížení standardní funkcí CRT, které volají bezpečnější variant automaticky. Pokud `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` je 1, pak je nutné provést žádné změny kódu. Na pozadí, volání `strcpy` se změní na volání `strcpy_s` s argumentem velikost zadaná automaticky.  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1  
  
// ...  
  
char szBuf[10];  
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")  
```  
  
Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` nemá vliv na funkce, které trvat počet, jako například `strncpy`. Chcete-li povolit šabloně přetížení pro funkce count, definovat `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` na 1. Než tak učiníte, ale ujistěte, že váš kód předá počet znaků, ne velikost vyrovnávací paměti (běžné chyby). Navíc kód, který po volání funkce není nutný, pokud je volána zabezpečené typu variant explicitně zapíše null zakončení na konci vyrovnávací paměti. Pokud potřebujete zkrácení chování, přečtěte si [_truncate –](../c-runtime-library/truncate.md).  
  
> [!NOTE]
>  Makro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` vyžaduje, aby `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` je také definován jako 1. Pokud `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` je definován jako 1 a `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` je definován jako 0, aplikace nebude provádět žádné šabloně přetížení.  
  
Když definujete `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` hodnotu 1, umožňuje šabloně přetížení variant zabezpečené (názvy končí na "_Malá"). V takovém případě pokud `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` je 1, pak jeden malých změn musí být provedeny na původní kód:  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1  
  
// ...  
  
char szBuf[10];  
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")  
```  
  
 Název funkce je potřeba změnit (přidáním "_Malá"); přetížení šablony postará poskytnout argument velikost.  
  
 Ve výchozím nastavení `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` a `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` jsou definovány jako 0 (zakázáno) a `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` je definován jako 1 (povoleno).  
  
 Všimněte si, že tyto šablony přetížení funguje jenom pro statické pole. Dynamicky přidělené vyrovnávací paměti vyžadovat změny další zdrojového kódu. Opětovné návštěvy uvedených příkladech:  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1  
  
// ...  
  
char *szBuf = (char*)malloc(10);  
strcpy(szBuf, "test"); // still deprecated; you have to change it to  
                       // strcpy_s(szBuf, 10, "test");  
```  
  
 A tato:  
  
```cpp  
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1  
  
// ...  
  
char *szBuf = (char*)malloc(10);  
strcpy_s(szBuf, "test"); // doesn't compile; you have to change it to  
                         // strcpy_s(szBuf, 10, "test");  
```  
  
## <a name="see-also"></a>Viz také  
 [Funkce zabezpečení v CRT](../c-runtime-library/security-features-in-the-crt.md)   
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)