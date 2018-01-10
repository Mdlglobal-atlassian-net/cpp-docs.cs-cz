---
title: "__security_init_cookie – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __security_init_cookie
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- security_init_cookie
- __security_init_cookie
dev_langs: C++
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee0657393ec8322889b527c21a36c13b9e032325
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="securityinitcookie"></a>__security_init_cookie
Inicializuje soubor cookie globálního zabezpečení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __security_init_cookie(void);  
```  
  
## <a name="remarks"></a>Poznámky  
 Soubor cookie globálního zabezpečení se používá k ochraně přetečení vyrovnávací paměti v kódu kompilovat s [/GS (Kontrola zabezpečení vyrovnávací paměti)](../../build/reference/gs-buffer-security-check.md) a v kódu, který používá výjimek. Na položku do funkce přetečení chráněný soubor cookie je uvést v zásobníku a při ukončení hodnota v zásobníku se porovná se globální souboru cookie. Případný rozdíl mezi nimi označuje, že došlo k přetečení vyrovnávací paměti a způsobí okamžité ukončení programu.  
  
 Za normálních okolností `__security_init_cookie` volá CRT při inicializaci. Pokud vyřazení inicializace CRT – například pokud použijete [/Entry](../../build/reference/entry-entry-point-symbol.md) k určení vstupního bodu – musí zavolat `__security_init_cookie` sami. Pokud `__security_init_cookie` není volán, na globální soubor cookie zabezpečení je nastaveno na výchozí hodnotu a dojde k narušení ochrany přetečení vyrovnávací paměti. Protože útočník může zneužít tuto výchozí hodnotu souboru cookie do jaké míry kontroly přetečení vyrovnávací paměti, doporučujeme vždy volat `__security_init_cookie` když definujete vlastní vstupní bod.  
  
 Volání `__security_init_cookie` je nutné provést před kteroukoli chráněné přetečení funkce se zadá; v opačném případě bude zjištěn přetečení nesprávné vyrovnávací paměti. Další informace najdete v tématu [C Runtime chyba R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklady v [C Runtime chyba R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`__security_init_cookie`|\<Process.h >|  
  
 `__security_init_cookie`je rozšíření Microsoft pro standardní běhové knihovny. Informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Podrobněji kontroly zabezpečení kompilátoru](http://go.microsoft.com/fwlink/p/?linkid=7260)