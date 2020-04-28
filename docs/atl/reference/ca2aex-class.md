---
title: CA2AEX – třída
ms.date: 11/04/2016
f1_keywords:
- CA2AEX
- ATLCONV/ATL::CA2AEX
- ATLCONV/ATL::CA2AEX::CA2AEX
- ATLCONV/ATL::CA2AEX::m_psz
- ATLCONV/ATL::CA2AEX::m_szBuffer
helpviewer_keywords:
- CA2AEX class
ms.assetid: 57dc65df-d9cf-4a84-99d3-6e031dde3664
ms.openlocfilehash: dfd8967d21005d83b38eeae36cfc147051d7beaf
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168524"
---
# <a name="ca2aex-class"></a>CA2AEX – třída

Tato třída je používána makry převodu řetězce CA2TEX a CT2AEX a typedef CA2A.

> [!IMPORTANT]
> Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
template <int t_nBufferLength = 128>
class CA2AEX
```

### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Velikost vyrovnávací paměti použité v procesu překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CA2AEX::CA2AEX](#ca2aex)|Konstruktor|
|[CA2AEX:: ~ CA2AEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CA2AEX:: operator typem LPStr](#operator_lpstr)|Operátor převodu|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CA2AEX:: m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|
|[CA2AEX:: m_szBuffer](#m_szbuffer)|Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.|

## <a name="remarks"></a>Poznámky

Pokud nejsou vyžadovány žádné další funkce, použijte CA2TEX, CT2AEX nebo CA2A ve vlastním kódu.

Tato třída obsahuje statickou vyrovnávací paměť pevné velikosti, která se používá k uložení výsledku převodu. Je-li výsledek příliš velký, aby se vešel do statické vyrovnávací paměti, třída přiděluje paměť **pomocí třídy**typu \ a uvolní paměť, když se objekt dostane mimo rozsah. Tím je zajištěno, že na rozdíl od maker převodu textu dostupných v předchozích verzích knihovny ATL je tato třída bezpečná pro použití ve smyčkách a její přetečení do zásobníku.

Pokud se třída pokusí přidělit paměť na haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.

Ve výchozím nastavení používají převodní třídy a makra knihovny ATL k převodu znakovou stránku ANSI aktuálního vlákna.

Následující makra jsou založena na této třídě:

- CA2TEX

- CT2AEX

Následující definice typedef je založena na této třídě:

- CA2A

Diskuzi o těchto makrech převodu textu viz [makra ATL a MFC String Conversion](string-conversion-macros.md).

## <a name="example"></a>Příklad

Příklad použití těchto maker převodů řetězců naleznete v tématech [ATL a makra převodu řetězců knihovny MFC](string-conversion-macros.md) .

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv. h

## <a name="ca2aexca2aex"></a><a name="ca2aex"></a>CA2AEX::CA2AEX

Konstruktor

```cpp
CA2AEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2AEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Textový řetězec, který má být převeden.

*nCodePage*<br/>
Nepoužitelné v této třídě.

### <a name="remarks"></a>Poznámky

Vytvoří vyrovnávací paměť požadovanou pro překlad.

## <a name="ca2aexca2aex"></a><a name="dtor"></a>CA2AEX:: ~ CA2AEX

Destruktor.

```cpp
~CA2AEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělenou vyrovnávací paměť.

## <a name="ca2aexm_psz"></a><a name="m_psz"></a>CA2AEX:: m_psz

Datový člen, který ukládá zdrojový řetězec.

```cpp
LPSTR m_psz;
```

## <a name="ca2aexm_szbuffer"></a><a name="m_szbuffer"></a>CA2AEX:: m_szBuffer

Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.

```cpp
char m_szBuffer[ t_nBufferLength];
```

## <a name="ca2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CA2AEX:: operator typem LPStr

Operátor převodu

```cpp
operator LPSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typ typem LPStr.

## <a name="see-also"></a>Viz také

[CA2CAEX – třída](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX – třída](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX – třída](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX – třída](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX – třída](../../atl/reference/cw2wex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
