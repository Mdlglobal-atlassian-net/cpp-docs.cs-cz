---
title: "iscsym –, iscsymf –, __iscsym –, __iswcsym –, __iscsymf –, __iswcsymf –, _iscsym_l –, _iswcsym_l –, _iscsymf_l –, _iswcsymf_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _iswcsym_l
- __iswcsym
- __iscsym
- _iswcsymf_l
- _iscsym_l
- __iswcsymf
- __iscsymf
- _iscsymf_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _iswcsym_l
- _iswcsymf_l
- iscsymf
- iswcsymf
- __iswcsym
- __iswcsymf
- iscsym
- iswcsym
- __iscsym
- _iscsym_l
- _iscsymf_l
- __iscsymf
- ctype/iscsym
- ctype/iscsymf
- ctype/__iscsym
- ctype/__iscsymf
- ctype/__iscsym_l
- ctype/__iscsymf_l
- ctype/__iswcsym
- ctype/__iswcsymf
- ctype/__iswcsym_l
- ctype/__iswcsymf_l
dev_langs: C++
helpviewer_keywords:
- iscsymf_l function
- iswsym_l function
- _iswcsym_l function
- iscsym_l function
- _iscsymf_l function
- _iswcsymf_l function
- _iscsym_l function
- __iscsym function
- __iswcsymf function
- iswsymf_l function
- __iscsymf function
- __iswcsym function
- iscsym function
- iscsymf function
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3567e6843fc3350d92c6575d320885298140ed50
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iscsym-iscsymf-iscsym-iswcsym-iscsymf-iswcsymf-iscsyml-iswcsyml-iscsymfl-iswcsymfl"></a>iscsym –, iscsymf –, __iscsym –, __iswcsym –, __iscsymf –, __iswcsymf –, _iscsym_l –, _iswcsym_l –, _iscsymf_l –, _iswcsymf_l –

Určení, pokud celé reprezentuje znak, který je možné použít identifikátor.

## <a name="syntax"></a>Syntaxe

```C
int __iscsym(
   int c
);
int __iswcsym(
   wint_t c
);
int __iscsymf(
   int c
);
int __iswcsymf(
   wint_t c
);
int _iscsym_l(
   int c,
   _locale_t locale
);
int _iswcsym_l(
   wint_t c,
   _locale_t locale
);
int _iscsymf_l(
   int c,
   _locale_t locale
);
int _iswcsymf_l(
   wint_t c,
   _locale_t locale
);
#define iscsym __iscsym
#define iscsymf __iscsymf
```

### <a name="parameters"></a>Parametry

*c*  
Celé číslo pro testování. *c* by měla být v rozsahu 0 až 255 úzké znak verze funkce.

*národní prostředí*  
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Obě `__iscsym` a `__iswcsym` vrátí nenulovou hodnotu, pokud *c* je písmeno, podtržítko nebo číslice. Obě `__iscsymf` a `__iswcsymf` vrátí nenulovou hodnotu, pokud *c* je písmenem nebo podtržítkem. Všechny tyto rutiny vrátí hodnotu 0, pokud *c* nesplňuje podmínky testu. Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že se používají *národního prostředí* předaná místo aktuální národní prostředí pro jejich chování závislých na národním prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

## <a name="remarks"></a>Poznámky

Tyto rutiny jsou definovány jako makra, pokud je definována _CTYPE_DISABLE_MACROS makro preprocesoru. Při použití makro verzích tyto rutiny argumenty, které lze vyhodnotit více než jednou. Buďte opatrní při použití výrazy, které mají vedlejší účinky v rámci seznamu argumentů.

Z důvodu zpětné kompatibility `iscsym` a `iscsymf` jsou definovány jako makra pouze tehdy, když [&#95; &#95; STDC &#95; &#95; ](../../preprocessor/predefined-macros.md) není definované nebo je definován jako 0; v opačném případě nejsou definovány.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`iscsym`, `iscsymf`, `__iscsym`, `__iswcsym`, `__iscsymf`, `__iswcsymf`, `_iscsym_l`, `_iswcsym_l`, `_iscsymf_l`, `_iswcsymf_l`|C: \<ctype.h ><br /><br /> C++: \<cctype – > nebo \<ctype.h >|

`iscsym`, `iscsymf`, `__iscsym`, `__iswcsym`, `__iscsymf`, `__iswcsymf`, `_iscsym_l`, `_iswcsym_l`, `_iscsymf_l`, A `_iswcsymf_l` rutiny se konkrétní společnosti Microsoft. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Klasifikace znaků](../../c-runtime-library/character-classification.md)   
[Národní prostředí](../../c-runtime-library/locale.md)   
[is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)