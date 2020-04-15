---
title: Třída CW2AEX
ms.date: 11/04/2016
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
ms.openlocfilehash: 849cbe5c26d7c7af7a8925a26057b5777554471d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330444"
---
# <a name="cw2aex-class"></a>Třída CW2AEX

Tato třída je používána makry převodu řetězce CT2AEX, CW2TEX, CW2CTEX a CT2CAEX a typedef CW2A.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>Parametry

*t_nBufferLength*<br/>
Velikost vyrovnávací paměti použité v procesu překladu. Výchozí délka je 128 bajtů.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|Konstruktor|
|[CW2AEX::~CW2AEX](#dtor)|Destruktor.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CW2AEX::operátor LPSTR](#operator_lpstr)|Operátor převodu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CW2AEX::m_psz](#m_psz)|Datový člen, který ukládá zdrojový řetězec.|
|[CW2AEX::m_szBuffer](#m_szbuffer)|Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.|

## <a name="remarks"></a>Poznámky

Pokud není vyžadována další funkce, použijte ct2AEX, CW2TEX, CW2CTEX, CT2CAEX nebo CW2A ve vašem kódu.

Tato třída obsahuje statickou vyrovnávací paměť s pevnou velikostí, která se používá k uložení výsledku převodu. Pokud je výsledek příliš velký a nevejde se do statické vyrovnávací paměti, třída přidělí paměť pomocí **malloc**, uvolnění paměti při objektu přejde mimo rozsah. Tím je zajištěno, že na rozdíl od makra převodu textu, které jsou k dispozici v předchozích verzích seznamu ATL, je tato třída bezpečná pro použití ve smyčkách a že nebude přetečení zásobníku.

Pokud se třída pokusí přidělit paměť na haldě a selže, bude volat `AtlThrow` s argumentem E_OUTOFMEMORY.

Ve výchozím nastavení používají třídy převodu a makra atl aktuální vlákno pro převod. Pokud chcete přepsat toto chování pro konkrétní převod, zadejte znakovou stránku jako druhý parametr konstruktoru pro třídu.

Následující makra jsou založeny na této třídě:

- ČT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

Následující typedef je založena na této třídě:

- CW2A

Diskuse o těchto marech převodu textu naleznete v tématu [ATL a Makra převodu řetězců knihovny MFC](string-conversion-macros.md).

## <a name="example"></a>Příklad

Příklad použití těchto makra převodu řetězců řetězce [knihovny ATL a knihovny MFC.](string-conversion-macros.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlconv.h

## <a name="cw2aexcw2aex"></a><a name="cw2aex"></a>CW2AEX::CW2AEX

Konstruktor

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Textový řetězec, který má být převeden.

*nCodePage*<br/>
Znaková stránka použitá k provedení převodu. Další podrobnosti naleznete v diskusi o parametrech znakové stránky pro funkci [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) ve funkci sady Windows SDK.

### <a name="remarks"></a>Poznámky

Přidělí vyrovnávací paměť použitou v procesu překladu.

## <a name="cw2aexcw2aex"></a><a name="dtor"></a>CW2AEX::~CW2AEX

Destruktor.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>Poznámky

Uvolní přidělenou vyrovnávací paměť.

## <a name="cw2aexm_psz"></a><a name="m_psz"></a>CW2AEX::m_psz

Datový člen, který ukládá zdrojový řetězec.

```
LPSTR m_psz;
```

## <a name="cw2aexm_szbuffer"></a><a name="m_szbuffer"></a>CW2AEX::m_szBuffer

Statická vyrovnávací paměť, která se používá k uložení převedeného řetězce.

```
char m_szBuffer[t_nBufferLength];
```

## <a name="cw2aexoperator-lpstr"></a><a name="operator_lpstr"></a>CW2AEX::operátor LPSTR

Operátor převodu.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí textový řetězec jako typ LPSTR.

## <a name="see-also"></a>Viz také

[Třída CA2AEX](../../atl/reference/ca2aex-class.md)<br/>
[Třída CA2CAEX](../../atl/reference/ca2caex-class.md)<br/>
[Třída CA2WEX](../../atl/reference/ca2wex-class.md)<br/>
[Třída CW2CWEX](../../atl/reference/cw2cwex-class.md)<br/>
[Třída CW2WEX](../../atl/reference/cw2wex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
