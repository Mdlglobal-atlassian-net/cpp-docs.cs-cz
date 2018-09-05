---
title: Ca2caex – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
dev_langs:
- C++
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 147814856e1e447894fd9826b9620ea8d762d48c
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764976"
---
# <a name="ca2caex-class"></a>Ca2caex – třída

Tato třída se používá řetězec převodních maker CA2CTEX CT2CAEX a definice typedef CA2CA.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>  
class CA2CAEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*  
Velikost vyrovnávací paměti používané při překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|Konstruktor|
|[CA2CAEX –:: ~ CA2CAEX –](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CA2CAEX::Operator LPCSTR](#operator_lpcstr)|Operátor převodu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CA2CAEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|

## <a name="remarks"></a>Poznámky

Pokud není vyžadována další funkce, pomocí CA2CTEX, CT2CAEX nebo CA2CA ve svém vlastním kódu.

Tato třída je bezpečné používat ve smyčkách a nebude přetečení zásobníku. Ve výchozím nastavení Převod třídy ATL a makra použije znakovou stránku ANSI aktuální vlákno pro převod.

Následující makra jsou založené na této třídě:

- CA2CTEX

- CT2CAEX

Následující definice typedef je založena na této třídě:

- CA2CA

Informace o těchto makrech převodu textu, naleznete v tématu [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md).

## <a name="example"></a>Příklad

Zobrazit [knihovny ATL a MFC – makra převodu řetězců](string-conversion-macros.md) příklad použití převodních maker tyto řetězce.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv.h

##  <a name="ca2caex"></a>  CA2CAEX::CA2CAEX

Konstruktor

```
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*  
Textový řetězec, který má být převeden.

*nCodePage*  
Nepoužívané v této třídě.

### <a name="remarks"></a>Poznámky

Vytvoří vyrovnávací paměti vyžadované pro převod.

##  <a name="dtor"></a>  CA2CAEX –:: ~ CA2CAEX –

Destruktor.

```
~CA2CAEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělené vyrovnávací paměti.

##  <a name="m_psz"></a>  CA2CAEX::m_psz

Datový člen, který ukládá zdrojový řetězec.

```
LPCSTR m_psz;
```

##  <a name="operator_lpcstr"></a>  CA2CAEX::Operator LPCSTR

Operátor převodu.

```  
operator LPCSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec psaní LPCSTR.

## <a name="see-also"></a>Viz také

[Ca2aex – třída](../../atl/reference/ca2aex-class.md)   
[Ca2wex – třída](../../atl/reference/ca2wex-class.md)   
[Cw2aex – třída](../../atl/reference/cw2aex-class.md)   
[Cw2cwex – třída](../../atl/reference/cw2cwex-class.md)   
[Cw2wex – třída](../../atl/reference/cw2wex-class.md)   
[Přehled tříd](../../atl/atl-class-overview.md)
