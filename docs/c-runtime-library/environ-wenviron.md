---
title: "_environ –, _wenviron – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- environ
- wenviron
- _wenviron
- _environ
dev_langs:
- C++
helpviewer_keywords:
- environ function
- _environ function
- _wenviron function
- process environment
- wenviron function
ms.assetid: 7e639962-6536-47cd-8095-0cbe44a56e03
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 277f8a853a5262d524016630f52bfcbfc8a8b18b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="environ-wenviron"></a>_environ, _wenviron
`_environ` Proměnné je ukazatel na pole ukazatele na řetězců vícebajtových znaků, které tvoří proces prostředí. Tato globální proměnná se už nepoužívá pro bezpečnější funkční verze [getenv_s –, _wgetenv_s –](../c-runtime-library/reference/getenv-s-wgetenv-s.md) a [_putenv_s –, _wputenv_s –](../c-runtime-library/reference/putenv-s-wputenv-s.md), který má být použit místo globální proměnné. `_environ` je v Stdlib.h deklarována.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
extern char **_environ;  
```  
  
## <a name="remarks"></a>Poznámky  
 V programu, který používá `main` funkce, `_environ` je inicializován při spuštění programu podle nastavení, které jsou převzaty z prostředí operačního systému. V prostředí se skládá z jedné nebo víc položek formuláře  
  
 `ENVVARNAME``=string`  
  
 `getenv_s` a `putenv_s` použít `_environ` proměnnou pro přístup a úpravu tabulky prostředí. Když `_putenv` je volána k přidání nebo odstranění nastavení prostředí v tabulce prostředí změny velikosti. Její umístění v paměti se může změnit v závislosti na požadavcích paměti programu. Hodnota `_environ` je automaticky upravována odpovídajícím způsobem.  
  
 `_wenviron` Proměnné deklarovány v Stdlib.h jako:  
  
```  
extern wchar_t **_wenviron;  
```  
  
 široká charakterová verze `_environ`. V programu, který používá `wmain` funkce, `_wenviron` je inicializován při spuštění programu podle nastavení, které jsou převzaty z prostředí operačního systému.  
  
 V programu, který používá `main`, `_wenviron` je původně `NULL` protože prostředí se skládá z řetězců vícebajtových znaků. Při prvním volání `_wgetenv` nebo `_wputenv`, odpovídající prostředí široká charakterová řetězec je vytvořen a je na kterou odkazuje `_wenviron`.  
  
 Podobně, v programu, který používá `wmain`, `_environ` je původně `NULL` protože prostředí se skládá z řetězce široká charakterová. Při prvním volání `_getenv` nebo `_putenv`, odpovídající řetězce vícebajtových znaků prostředí je vytvořen a je na kterou odkazuje `_environ`.  
  
 Pokud dvě kopie prostředí (MBCS a Unicode) existují současně v programu, musíte udržovat běhu systému obě kopie, výsledkem je pomalejší dobu provádění. Například když zavoláte `_putenv`, volání `_wputenv` je také provést automaticky, takže odpovídají řetězce dvě prostředí.  
  
> [!CAUTION]
>  Ve výjimečných případech při běhu systému údržbu Unicode verze a vícebajtové verzi prostředí, tyto dvě prostředí verze nemusí odpovídat přesně. Je to proto, i když všechny jedinečné řetězce vícebajtových znaků se mapuje na jedinečné řetězce Unicode, mapování z jedinečné řetězce Unicode do řetězce vícebajtových znaků není nutně jedinečný. Proto může na stejném řetězci vícebajtové mapovat dvě odlišné řetězců v kódu Unicode.  
  
 Dotazování `_environ` v typu Unicode kontextu je smysl při [/MD](../build/reference/md-mt-ld-use-run-time-library.md) nebo `/MDd` slouží k propojení. Typ (celou nebo vícebajtové) programu pro knihovnu DLL CRT neznámý. Pouze typ vícebajtové je vytvořit, protože to je nejpravděpodobnější scénář.  
  
 Pseudo následující kód ukazuje, jak tomu může dojít.  
  
```  
int i, j;  
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:  
                                      // putenv ("env_var_z=string1")  
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:  
                                      // putenv("env_var_z=string2")  
```  
  
 V tomto příkladu používá notaci řetězců znaků nejsou textové literály jazyka C; Namísto toho jsou zástupné symboly, které představují Unicode prostředí textové literály v `_wputenv` volání a vícebajtových prostředí řetězců v `putenv` volání. Zástupný znak text`x`'a'`y`' ve dvou různých Unicode prostředí řetězce nemapovaly jednoznačně znaků v aktuální MBCS. Místo toho obě namapovány na některé MBCS znak '`z`, který je výchozím výsledkem pokusu o převod řetězce.  
  
 Proto v vícebajtové prostředí hodnotu "`env_var_z`" po prvním implicitní volání `putenv` by "`string1`", ale tuto hodnotu budou přepsána na druhý implicitní volání `putenv`, když hodnota "`env_var_z`" je Nastavte na "`string2`". Prostředí Unicode (v `_wenviron`) a vícebajtové prostředí (v `_environ`) by se proto liší následující tuto řadu volání.  
  
## <a name="see-also"></a>Viz také  
 [Globální proměnné](../c-runtime-library/global-variables.md)   
 [getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)   
 [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)   
 [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)