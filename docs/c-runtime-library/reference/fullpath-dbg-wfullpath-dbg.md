---
title: _fullpath_dbg –, _wfullpath_dbg – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wfullpath_dbg
- _fullpath_dbg
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
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
dev_langs:
- C++
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d04f3d7b53eca27d38a38b0bce284c17b15cae02
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450892"
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg, _wfullpath_dbg

Verze [_fullpath –, _wfullpath –](fullpath-wfullpath.md) , použijte ladicí verzi **malloc** přidělit paměť.

## <a name="syntax"></a>Syntaxe

```C
char *_fullpath_dbg(
   char *absPath,
   const char *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wfullpath_dbg(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parametry

*absPath*<br/>
Ukazatel na vyrovnávací paměť obsahující název absolutní nebo úplné cesty, nebo **NULL**.

*relPath*<br/>
Relativní cesta.

*Hodnota maxLength*<br/>
Maximální délka vyrovnávací paměť názvu absolutní cestu (*absPath*). Se délka v bajtech pro **_fullpath –** , ale v široké znaky (**wchar_t**) pro **_wfullpath –**.

*blockType*<br/>
Požadovaný typ bloku paměti: **_client_block –** nebo **_normal_block –**.

*Název souboru*<br/>
Ukazatel na název zdrojového souboru, který požadovanou operaci přidělení nebo **NULL**.

*lineNumber*<br/>
Číslo řádku na zdrojový soubor, kde byla vyžádána operace přidělení nebo **NULL**.

## <a name="return-value"></a>Návratová hodnota

Jednotlivé funkce vrátí ukazatel do vyrovnávací paměti obsahující absolutní cesta (*absPath*). Pokud dojde k chybě (například pokud je předaná hodnota *relPath* zahrnuje písmeno jednotky, které není platná nebo nebyla nalezena, nebo pokud délka názvu vytvořený absolutní cestu (*absPath*) je větší než *maxLength*) funkce vrátí hodnotu **NULL**.

## <a name="remarks"></a>Poznámky

**_Fullpath_dbg –** a **_wfullpath_dbg –** funkce jsou stejné jako **_fullpath –** a **_wfullpath –** s tím rozdílem, že když **_DEBUG –** je definován, tyto funkce používají verzi ladění **malloc –**, **_malloc_dbg –**, přidělit paměť, pokud **NULL** je předán jako první parametr. Informace o ladění funkce **_malloc_dbg –**, najdete v části [_malloc_dbg –](malloc-dbg.md).

Není nutné explicitně volat tyto funkce ve většině případů. Místo toho můžete definovat **_crtdbg_map_alloc –** příznak. Když **_crtdbg_map_alloc –** je definován, volání **_fullpath –** a **_wfullpath –** jsou mapovány na **_fullpath_dbg –** a **_wfullpath_dbg –**, s *blockType* nastavena na **_normal_block –**. Proto není nutné explicitně volat tyto funkce, pokud chcete označit bloky haldy jako **_client_block –**. Další informace najdete v tématu [typy bloků v haldě ladění](/visualstudio/debugger/crt-debug-heap-details).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[Zpracování souborů](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[Ladění verzí funkcí přidělení haldy](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
