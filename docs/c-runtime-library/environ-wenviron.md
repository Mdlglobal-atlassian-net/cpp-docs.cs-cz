---
title: _environ, _wenviron
ms.date: 11/04/2016
f1_keywords:
- environ
- wenviron
- _wenviron
- _environ
helpviewer_keywords:
- environ function
- _environ function
- _wenviron function
- process environment
- wenviron function
ms.assetid: 7e639962-6536-47cd-8095-0cbe44a56e03
ms.openlocfilehash: 8d67947c93d1387bfdc38c3bae5b3f978024a725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349371"
---
# <a name="_environ-_wenviron"></a>_environ, _wenviron

Proměnná `_environ` je ukazatel na pole ukazatelů na vícebajtové řetězce znaků, které tvoří prostředí procesu. Tato globální proměnná byla zastaralá pro bezpečnější funkční verze [getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md) a [_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md), které by měly být použity místo globální proměnné. `_environ`je deklarována v Stdlib.h.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```
extern char **_environ;
```

## <a name="remarks"></a>Poznámky

V programu, který `main` používá `_environ` funkci, je inicializován při spuštění programu podle nastavení převzatých z prostředí operačního systému. Životní prostředí se skládá z jedné nebo více položek formuláře

`ENVVARNAME` `=string`

`getenv_s`a `putenv_s` použít `_environ` proměnnou pro přístup a úpravu tabulky prostředí. Když `_putenv` je volána přidat nebo odstranit nastavení prostředí, tabulka prostředí změní velikost. Jeho umístění v paměti se může také změnit v závislosti na požadavcích programu na paměť. Hodnota `_environ` je automaticky upravena odpovídajícím způsobem.

Proměnná `_wenviron` deklarovaná v Stdlib.h jako:

```
extern wchar_t **_wenviron;
```

je širokoznaková verze `_environ`aplikace . V programu, který `wmain` používá `_wenviron` funkci, je inicializován při spuštění programu podle nastavení převzatých z prostředí operačního systému.

V programu, `main`který `_wenviron` používá , je zpočátku **NULL,** protože prostředí se skládá z vícebajtových řetězců znaků. Při prvním volání `_wgetenv` `_wputenv`nebo je vytvořeno odpovídající prostředí řetězce s širokými znaky, na které je odkazováno . `_wenviron`

Podobně v programu, který `wmain` `_environ` používá , je zpočátku **NULL,** protože prostředí se skládá z řetězců širokých znaků. Při prvním volání `_getenv` `_putenv`nebo je vytvořeno odpovídající vícebajtové prostředí řetězce `_environ`a je odkazováno .

Pokud v programu existují současně dvě kopie prostředí (MBCS a Unicode), musí systém za běhu udržovat obě kopie, což má za následek pomalejší dobu provádění. Například při každém `_putenv`volání , `_wputenv` volání je také automaticky spuštěna tak, aby dva řetězce prostředí odpovídají.

> [!CAUTION]
> Ve výjimečných případech, kdy systém run-time udržuje verzi Unicode i vícebajtovou verzi prostředí, nemusí tyto dvě verze prostředí přesně odpovídat. Je to proto, že i když každý jedinečný vícebajtový řetězec se mapuje na jedinečný řetězec Unicode, mapování z jedinečného řetězce Unicode na vícebajtový řetězec není nutně jedinečné. Proto dva odlišné řetězce Unicode může mapovat na stejný vícebajtový řetězec.

Dotazování `_environ` v kontextu Unicode je bezvýznamné `/MDd` při použití [/MD](../build/reference/md-mt-ld-use-run-time-library.md) nebo propojení. Pro crt dll typ (široký nebo vícebajtový) programu není znám. Je vytvořen pouze vícebajtový typ, protože to je nejpravděpodobnější scénář.

Následující pseudo-kód ukazuje, jak k tomu může dojít.

```
int i, j;
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:
                                      // putenv ("env_var_z=string1")
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:
                                      // putenv("env_var_z=string2")
```

V zápisu použitém pro tento příklad nejsou řetězce znaků literály řetězce C; spíše jsou zástupné symboly, které představují literály řetězce prostředí Unicode `_wputenv` ve `putenv` volání a vícebajtové řetězce prostředí ve volání. Zástupné symboly`x`znaků`y`" " a ' ve dvou odlišných řetězcích prostředí Unicode nejsou jednoznačně mapovány na znaky v aktuální mbcs. Místo toho obě mapovat na`z`některé znak MBCS ' to je výchozí výsledek pokusu o převod řetězců.

Proto v vícebajtovém prostředí hodnota`env_var_z`" " po `putenv` prvním implicitním volání by byla`string1`" ", ale `putenv`tato hodnota by`env_var_z`byla přepsána`string2`při druhém implicitním volání do , když je hodnota " " nastavena na " ". Prostředí Unicode (v `_wenviron`) a vícebajtové prostředí (v `_environ`) by se proto lišit po této sérii volání.

## <a name="see-also"></a>Viz také

[Globální proměnné](../c-runtime-library/global-variables.md)<br/>
[getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s, _wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s, _wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)
