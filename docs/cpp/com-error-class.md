---
title: _com_error – třída
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 8ed1521cbf768e5b473281e5f9b7c6597cdc4692
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155199"
---
# <a name="comerror-class"></a>_com_error – třída

**Microsoft Specific**

A **_com_error** objekt představuje podmínku výjimky vyhledat pomocí funkce obálky zpracování chyb v souborech hlaviček generovaných z knihovny typů nebo jeden z třídy COM support. **_Com_error** třída zapouzdří kód chyby: HRESULT a všechny přidružené `IErrorInfo Interface` objektu.

### <a name="construction"></a>Konstrukce

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Vytvoří **_com_error** objektu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](../cpp/com-error-operator-equal.md)|Přiřadí existující **_com_error** objektu na jiný.|

### <a name="extractor-functions"></a>Extraktor funkcí

|||
|-|-|
|[Chyba](../cpp/com-error-error.md)|Načte hodnotu HRESULT předaný konstruktoru.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|Načte `IErrorInfo` objekt předaný konstruktoru.|
|[WCode](../cpp/com-error-wcode.md)|Načte 16bitové chybový kód namapovat na zapouzdřený HRESULT.|

### <a name="ierrorinfo-functions"></a>Funkce IErrorInfo

|||
|-|-|
|[Popis](../cpp/com-error-description.md)|Volání `IErrorInfo::GetDescription` funkce.|
|[HelpContext](../cpp/com-error-helpcontext.md)|Volání `IErrorInfo::GetHelpContext` funkce.|
|[HelpFile](../cpp/com-error-helpfile.md)|Volání `IErrorInfo::GetHelpFile` – funkce|
|[Zdroj](../cpp/com-error-source.md)|Volání `IErrorInfo::GetSource` funkce.|
|[GUID](../cpp/com-error-guid.md)|Volání `IErrorInfo::GetGUID` funkce.|

### <a name="format-message-extractor"></a>Formát zprávy Extraktor

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|Získá řetězcovou zprávu pro HRESULT uložený ve **_com_error** objektu.|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode k Mapovačů HRESULT

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Mapuje 32-bit HRESULT na 16 bitů `wCode`.|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapuje 16bitové `wCode` 32-bit HRESULT.|

**Specifické pro END Microsoft**

## <a name="requirements"></a>Požadavky

**Header:** \<comdef.h>

`Lib:` comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Další informace)

## <a name="see-also"></a>Viz také:

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)<br/>
[Rozhraní IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)