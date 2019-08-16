---
title: _com_error – třída
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 828a1ec68fef631700d5b64e6aeeec6660acf9a8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498749"
---
# <a name="_com_error-class"></a>_com_error – třída

**Specifické pro společnost Microsoft**

Objekt **_com_error** představuje podmínku výjimky zjištěné funkcemi obálky zpracování chyb v hlavičkových souborech generovaných z knihovny typů nebo pomocí jedné z tříd podpory modelu COM. Třída **_com_error** zapouzdřuje kód chyby HRESULT a všechny přidružené `IErrorInfo Interface` objekty.

### <a name="construction"></a>Stavbě

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|Vytvoří objekt **_com_error** .|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](../cpp/com-error-operator-equal.md)|Přiřadí existující objekt **_com_error** k druhému.|

### <a name="extractor-functions"></a>Funkce extraktoru

|||
|-|-|
|[Chyba](../cpp/com-error-error.md)|Načte HRESULT předaný konstruktoru.|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|`IErrorInfo` Načte objekt předaný konstruktoru.|
|[WCode](../cpp/com-error-wcode.md)|Načte 16bitový kód chyby mapovaný do zapouzdřené hodnoty HRESULT.|

### <a name="ierrorinfo-functions"></a>Funkce IErrorInfo

|||
|-|-|
|[Popis](../cpp/com-error-description.md)|Funkce `IErrorInfo::GetDescription` Call.|
|[Atribut HelpContext](../cpp/com-error-helpcontext.md)|Funkce `IErrorInfo::GetHelpContext` Call.|
|[Soubor](../cpp/com-error-helpfile.md)|Funkce `IErrorInfo::GetHelpFile` Call|
|[Zdroj](../cpp/com-error-source.md)|Funkce `IErrorInfo::GetSource` Call.|
|[GUID](../cpp/com-error-guid.md)|Funkce `IErrorInfo::GetGUID` Call.|

### <a name="format-message-extractor"></a>Formátovat extraktor zpráv

|||
|-|-|
|[Chybová](../cpp/com-error-errormessage.md)|Načte řetězcovou zprávu pro HRESULT uloženou v objektu **_com_error** .|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo. wCode na mapovače HRESULT

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|Mapuje 32-bit HRESULT na 16 bitů `wCode`.|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|Mapuje 16 bitů `wCode` na 32-bit HRESULT.|

**Specifické pro konec Microsoftu**

## <a name="requirements"></a>Požadavky

**Hlavička:** \<Comdef. h >

`Lib:`comsuppw. lib nebo comsuppwd. lib (Další informace naleznete v tématu [/Zc: wchar_t (Wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>Viz také:

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)<br/>
[Rozhraní IErrorInfo](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)