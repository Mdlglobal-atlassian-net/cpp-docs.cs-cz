---
title: _com_ptr_t::CreateInstance | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa81e25b30061881dc00a401dc386647a8cdb73b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094231"
---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance

**Specifické pro Microsoft**

Vytvoří novou instanci objektu dle `CLSID` nebo `ProgID`.

## <a name="syntax"></a>Syntaxe

```
HRESULT CreateInstance(
   const CLSID& rclsid,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCWSTR clsidString,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCSTR clsidStringA,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
```

#### <a name="parameters"></a>Parametry

*rclsid*<br/>
`CLSID` Objektu.

*clsidString*<br/>
Řetězec znaků Unicode udržující `CLSID` (počínaje "**{**") nebo `ProgID`.

*clsidStringA*<br/>
Vícebajtový řetězec používající znakovou stránku ANSI, který udržuje `CLSID` (počínaje "**{**") nebo `ProgID`.

*dwClsContext*<br/>
Kontext spuštění spustitelného kódu.

*pOuter*<br/>
Vnější Neznámá pro [agregace](../atl/aggregation.md).

## <a name="remarks"></a>Poznámky

Tyto členské funkce volají `CoCreateInstance` k vytvoření nového objektu modelu COM a pak dotazů pro typ rozhraní tohoto inteligentního ukazatele. Výsledný ukazatel je pak zapouzdřen v tomto objektu `_com_ptr_t`. `Release` nazývá se sníží počet odkazů na dříve zapouzdřený ukazatel. Tato rutina vrátí hodnotu HRESULT indikuje úspěch nebo selhání.

- **Funkci CreateInstance (***rclsid* **,***dwClsContext***)** vytvoří novou běžící instanci objektu dle `CLSID`.

- **Funkci CreateInstance (***clsidString* **,***dwClsContext***)** vytvoří novou běžící instanci objektu dle Řetězec znaků Unicode udržující `CLSID` (počínaje "**{**") nebo `ProgID`.

- **Funkci CreateInstance (***clsidStringA* **,***dwClsContext***)** vytvoří novou běžící instanci objektu dle vícebajtový řetězec udržující `CLSID` (počínaje "**{**") nebo `ProgID`. Volání [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar), kde se předpokládá, že je řetězec uložen ve znakovou stránku ANSI, nikoli znakovou stránku OEM.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[_com_ptr_t – třída](../cpp/com-ptr-t-class.md)