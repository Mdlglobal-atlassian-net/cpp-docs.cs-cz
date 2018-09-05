---
title: Cw2cwex – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CW2CWEX
- ATLCONV/ATL::CW2CWEX
- ATLCONV/ATL::CW2CWEX::CW2CWEX
- ATLCONV/ATL::CW2CWEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CW2CWEX class
ms.assetid: d654b22b-05a6-410f-a0ec-9a2cbbb4cca7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee4314e4f2d31e499c01049d1fbec579f16c2849
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765359"
---
# <a name="cw2cwex-class"></a>Cw2cwex – třída

Tato třída se používá makra převodu řetězců CW2CTEX CT2CWEX a definice typedef CW2W.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>  
class CW2CWEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*  
Velikost vyrovnávací paměti používané při překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CW2CWEX::CW2CWEX](#cw2cwex)|Konstruktor|
|[CW2CWEX –:: ~ CW2CWEX –](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CW2CWEX::Operator LPCWSTR](#operator_lpcwstr)|Operátor převodu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CW2CWEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|

## <a name="remarks"></a>Poznámky

Pokud není vyžadována další funkce, použití CW2CTEX, CT2CWEX nebo CW2W ve vašem kódu.

Tato třída je bezpečné používat ve smyčkách a nebude přetečení zásobníku. Ve výchozím nastavení používají převodu třídy ATL a makra znakovou stránku ANSI aktuální vlákno pro převod.

Následující makra jsou založené na této třídě:

- CW2CTEX

- CT2CWEX

Následující definice typedef je založena na této třídě:

- CW2W

Informace o těchto makrech převodu textu, naleznete v tématu [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md).

## <a name="example"></a>Příklad

Zobrazit [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv.h

##  <a name="cw2cwex"></a>  CW2CWEX::CW2CWEX

Konstruktor

```
CW2CWEX(LPCWSTR psz, UINT nCodePage) throw(...);  
CW2CWEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*  
Textový řetězec, který má být převeden.

*nCodePage*  
Znakovou stránku. Nepoužívá se v této třídě.

### <a name="remarks"></a>Poznámky

Přidělí vyrovnávací paměti používané při překladu.

##  <a name="dtor"></a>  CW2CWEX –:: ~ CW2CWEX –

Destruktor.

```
~CW2CWEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělené vyrovnávací paměti.

##  <a name="m_psz"></a>  CW2CWEX::m_psz

Datový člen, který ukládá zdrojový řetězec.

```
LPCWSTR m_psz;
```

##  <a name="operator_lpcwstr"></a>  CW2CWEX::Operator LPCWSTR

Operátor převodu.

```  
operator LPCWSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec psaní LPCWSTR.

## <a name="see-also"></a>Viz také

[Ca2aex – třída](../../atl/reference/ca2aex-class.md)   
[Ca2caex – třída](../../atl/reference/ca2caex-class.md)   
[Ca2wex – třída](../../atl/reference/ca2wex-class.md)   
[Cw2aex – třída](../../atl/reference/cw2aex-class.md)   
[Cw2wex – třída](../../atl/reference/cw2wex-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
