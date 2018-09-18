---
title: _environ _wenviron | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59ec0a0279c0b43b6ffdc1e5f25616c916624be2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018350"
---
# <a name="environ-wenviron"></a>_environ, _wenviron

`_environ` Proměnná je ukazatel na pole ukazatelů na vícebajtové znakové řetězce, které tvoří prostředí procesu. Tato globální proměnná se už nepoužívá pro bezpečnější funkční verze [getenv_s – _wgetenv_s –](../c-runtime-library/reference/getenv-s-wgetenv-s.md) a [_putenv_s _wputenv_s –](../c-runtime-library/reference/putenv-s-wputenv-s.md), který by měl být zastoupen globální proměnnou. `_environ` je deklarován v Stdlib.h.

> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```
extern char **_environ;
```

## <a name="remarks"></a>Poznámky

V programu v jazyce, který používá `main` funkci `_environ` je inicializován při spuštění programu podle nastavení z prostředí operačního systému. Prostředí se skládá z jedné nebo více položek ve formuláři

`ENVVARNAME``=string`

`getenv_s` a `putenv_s` použít `_environ` proměnné pro přístup a úpravy v tabulce prostředí. Když `_putenv` je volána k přidání nebo odstranění nastavení prostředí v tabulce prostředí změní velikost. Jeho umístění v paměti se může změnit v závislosti na požadavcích paměti programu. Hodnota `_environ` je automaticky upravována odpovídajícím způsobem.

`_wenviron` Proměnné deklarované v knihovně Stdlib.h jako:

```
extern wchar_t **_wenviron;
```

je širokoznaká verze `_environ`. V programu v jazyce, který používá `wmain` funkci `_wenviron` je inicializován při spuštění programu podle nastavení z prostředí operačního systému.

V programu v jazyce, který používá `main`, `_wenviron` je zpočátku **NULL** protože prostředí se skládá z vícebajtové znakové řetězce. Při prvním volání `_wgetenv` nebo `_wputenv`, odpovídající prostředí řetězce širokého znaku se vytvoří a ukazuje `_wenviron`.

Podobně, v programu v jazyce, který používá `wmain`, `_environ` je zpočátku **NULL** protože prostředí se skládá z řetězce širokého znaku. Při prvním volání `_getenv` nebo `_putenv`, odpovídající prostředí řetězce vícebajtových znaků se vytvoří a ukazuje `_environ`.

Pokud dvě kopie prostředí (znaková sada MBCS a Unicode) existují současně v programu v jazyce, za běhu systému, musíte mít obě kopie, což vede k času provádění. Například pokaždé, když voláte `_putenv`, volání `_wputenv` také provádí automaticky, takže odpovídají řetězce dvě prostředí.

> [!CAUTION]
>  Ve výjimečných případech při údržbě systému za běhu Unicode verze a vícebajtová verze prostředí, tyto dvě prostředí verze nemusí odpovídat přesně. Důvodem je, že i když jakýkoli jedinečný řetězec vícebajtového znaku zakončeného mapuje na jedinečné řetězec znaků Unicode, mapování z jedinečný řetězec znaků Unicode na řetězec vícebajtového znaku není nutně jedinečné. Proto dva odlišné řetězce Unicode mohou být mapovány na stejné vícebajtový řetězec.

Dotazování `_environ` v Unicode je kontext význam při [/MD](../build/reference/md-mt-ld-use-run-time-library.md) nebo `/MDd` propojení se používá. Pro knihovnu DLL CRT typ (celou nebo vícebajtový) programu neznámý. Pouze typ vícebajtového je vytvořit, protože to je nejpravděpodobnější scénář.

Pseudo následující kód ukazuje, jak k tomu může dojít.

```
int i, j;
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:
                                      // putenv ("env_var_z=string1")
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:
                                      // putenv("env_var_z=string2")
```

V notaci používané v tomto příkladu znakové řetězce nejsou textové literály jazyka C; Namísto toho jsou zástupné symboly, které představují řetězcové literály Unicode prostředí v `_wputenv` prostředí volání a vícebajtové řetězce v `putenv` volání. Zástupné symboly znaku`x`"a"`y`' ve dvou různých Unicode řetězců prostředí nemapovaly jednoznačně znaků v aktuální znakové sady MBCS. Místo toho obě namapovány na některé znaky znakové sady MBCS "`z`", který je výchozí výsledek pokusu o převedení řetězce.

Proto ve vícebajtové prostředí hodnotu "`env_var_z`" po prvním volání implicitní `putenv` by "`string1`", ale v druhé implicitní volání přepíše se tato hodnota `putenv`, když hodnota "`env_var_z`" je Nastavte na "`string2`". Prostředí kódování Unicode (v `_wenviron`) a vícebajtové prostředí (v `_environ`) by proto se liší podle této sérii volání.

## <a name="see-also"></a>Viz také

[Globální proměnné](../c-runtime-library/global-variables.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)