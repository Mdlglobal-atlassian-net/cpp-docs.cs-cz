---
title: CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows
ms.date: 12/30/2016
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
ms.openlocfilehash: 763d76dd9eb139c10f4147e5fa069a0901fe5398
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694124"
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows

Při sestavování aplikací univerzální platformy Windows (UPW), nejsou k dispozici mnoho funkcí jazyka C runtime (CRT). V některých případech jsou k dispozici alternativní řešení – – například můžete použít prostředí Windows Runtime nebo rozhraní API systému Win32. Ale v jiných případech funkce CRT zakázali vzhledem k tomu, že funkce, které odpovídají jejich nebo podpory rozhraní API se nevztahují na aplikacích pro UPW. Vyhledejte alternativní metodu, která je podporována pro prostředí Windows Runtime, najdete v článku [alternativy k rozhraní API Windows v aplikacích pro UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

V následující tabulce jsou uvedeny funkce CRT, které nejsou dostupné při vytváření aplikací pro UWP a označuje žádné alternativní řešení, které se vztahují.

## <a name="unsupported-crt-functions"></a>Nepodporovaná CRT – funkce

||||
|-|-|-|
|_beep _sleep _seterrormode|Tyto funkce se v předchozích verzích CRT zastaralé. Odpovídající rozhraní Win32 API nejsou k dispozici pro aplikace pro UPW.|Alternativní řešení neexistuje.|
|getcwd chdir _chdrive – –|Tyto funkce jsou zastaralé nebo nejsou bezpečné pro vlákna.|_Chdir – použití _getcwd a související funkce.|
|_cgets _cgets_s _cgetws _cgetws_s _cprintf _cprintf_l _cprintf_p _cprintf_p_l _cprintf_s _cprintf_s_l _cputs _cputws _cscanf _cscanf_l _cscanf_s _cscanf_s_l _cwait _cwprintf _cwprintf_l _cwprintf_p _cwprintf_p_l _cwprintf_s _cwprintf_s_l _cwscanf _cwscanf_l _cwscanf_s _cwscanf_s_l _vcprintf _vcprintf_l _vcprintf_p _vcprintf_p_l _vcprintf_s _vcprintf_s_l _vcwprintf _vcwprintf_l _vcwprintf_p _vcwprintf_p_l _vcwprintf_s _vcwprintf_s_l _getch _getch_nolock _getche _getche_nolock _getwch _getwch_nolock _getwche _getwche_nolock _putch _putch_nolock _putwch _putwch_nolock _ungetch _ungetch_nolock _ungetwch _ungetwch_nolock _kbhit kbhit putch cgets cprintf cputs cscanf cwait getch getche ungetch|Tyto funkce slouží ke čtení a zápisu přímo z a do konzoly. Aplikace UWP jsou grafického uživatelského rozhraní. nepodporují konzoly.|Alternativní řešení neexistuje.|
|getpid|Tato funkce je zastaralá.|Použijte _getpid – rozhraní API systému Win32 `GetCurrentProcessId()`.|
|_getdiskfree|Není k dispozici.|Použití rozhraní API systému Win32 `GetDiskFreeSpaceExW()`.|
|_getdrives _getdrive – –|Odpovídající rozhraní API není k dispozici pro aplikace pro UPW.|Alternativní řešení neexistuje.|
|_inp – _inpd – _inpw – _outp – _outpd – _outpw – inp inpd – inpw – outp – outpd – outpw –|Port vstupně-výstupní operace se nepodporuje v aplikacích pro UPW.|Alternativní řešení neexistuje.|
|_ismbcalnum _ismbcalnum_l _ismbcalpha _ismbcalpha_l _ismbcdigit _ismbcdigit_l _ismbcgraph _ismbcgraph_l _ismbchira _ismbchira_l _ismbckata _ismbckata_l _ismbcl0 _ismbcl0_l _ismbcl1 _ismbcl1_l _ismbcl2 _ismbcl2_l _ismbclegal _ismbclegal_l _ismbclower _ismbclower_l _ismbcprint _ismbcprint_l _ismbcpunct _ismbcpunct_l _ismbcspace _ismbcspace_l _ismbcsymbol _ismbcsymbol_l _ismbcupper _ismbcupper_l _mbbtombc _mbbtombc_l _mbbtype _mbbtype_l _mbccpy _mbccpy_l _mbccpy_s _mbccpy_s_l _mbcjistojms _mbcjistojms_l _mbcjmstojis _mbcjmstojis_l _mbclen _mbclen_l _mbctohira _mbctohira_l _mbctokata _mbctokata_l _mbctolower _mbctolower_l _mbctombb _mbctombb_l _mbctoupper _mbctoupper_l _mbsbtype _mbsbtype_l _mbscat _mbscat_l _mbscat_s _mbscat_s_l _mbschr _mbschr_l _mbscmp _mbscmp_l _mbscoll _mbscoll_l _mbscpy _mbscpy_l _mbscpy_s _mbscpy_s_l _mbscspn _mbscspn_l _mbsdec _mbsdec_l _mbsicmp _mbsicmp_l _mbsicoll _mbsicoll_l _mbsinc _mbsinc_l _mbslen _mbslen_l _mbslwr _mbslwr_l _mbslwr_s _mbslwr_s_l _mbsnbcat _mbsnbcat_l _mbsnbcat_s _mbsnbcat_s_l _mbsnbcmp _mbsnbcmp_l _mbsnbcnt _mbsnbcnt_l _mbsnbcoll _mbsnbcoll_l _mbsnbcpy _mbsnbcpy_l _mbsnbcpy_s _mbsnbcpy_s_l _mbsnbicmp _mbsnbicmp_l _mbsnbicoll _mbsnbicoll_l _mbsnbset _mbsnbset_l _mbsnbset_s _mbsnbset_s_l _mbsncat _mbsncat_l _mbsncat_s _mbsncat_s_l _mbsnccnt _mbsnccnt_l _mbsncmp _mbsncmp_l _mbsncoll _mbsncoll_l _mbsncpy _mbsncpy_l _mbsncpy_s _mbsncpy_s_l _mbsnextc _mbsnextc_l _mbsnicmp _mbsnicmp_l _mbsnicoll _mbsnicoll_l _mbsninc _mbsninc_l _mbsnlen _mbsnlen_l _mbsnset _mbsnset_l _mbsnset_s _mbsnset_s_l _mbspbrk _mbspbrk_l _mbsrchr _mbsrchr_l _mbsrev _mbsrev_l _mbsset _mbsset_l _mbsset_s _mbsset_s_l _mbsspn _mbsspn_l _mbsspnp _mbsspnp_l _mbsstr _mbsstr_l _mbstok _mbstok_l _mbstok_s _mbstok_s_l _mbsupr _mbsupr_l _mbsupr_s _mbsupr_s_l is_wctype|Vícebajtové řetězce nejsou podporovány v aplikacích pro UPW.|Místo toho použijte řetězců v kódu Unicode.|
|_wpopen _pclose – _pipe – _popen – –|Funkce kanálu není k dispozici pro aplikace UPW.|Alternativní řešení neexistuje.|
|_resetstkoflw|Podpůrné rozhraní Win32 API nejsou k dispozici pro aplikace pro UPW.|Alternativní řešení neexistuje.|
|_getsystime _setsystime|Byly zastaralé rozhraní API v předchozích verzích CRT. Také nemůže uživatel nastavení systémového času v aplikaci UWP z důvodu nedostatku oprávnění.|Systémový čas jenom získáte pomocí rozhraní API systému Win32 `GetSystemTime`. Systémový čas nelze nastavit.|
|_environ _putenv _putenv_s _searchenv _searchenv_s – _dupenv_s – _wputenv _wputenv_s – _wsearchenv getenv getenv_s – putenv _wdupenv_s – _wenviron _wgetenv _wgetenv_s – _wsearchenv_s – tzset –|Proměnné prostředí nejsou k dispozici pro aplikace UPW.|Alternativní řešení neexistuje. Pokud chcete nastavit časové pásmo, použijte _tzset –.|
|_loaddll _getdllprocaddr _unloaddll|Byly zastaralé funkce v předchozích verzích CRT. Uživatel také nelze načíst knihovny DLL s výjimkou od těch, které ve stejném balíčku aplikace.|Použití rozhraní API Win32 `LoadPackagedLibrary`, `GetProcAddress`, a `FreeLibrary` načtení a použití zabalené knihovny DLL.|
|_wexecl – _wexecle – _wexeclp – _wexeclpe – _wexecv – _wexecve – _wexecvp – _wexecvpe – _execl _execle – _execlp – _execlpe – _execv _execve _execvp – _execvpe _spawnl _spawnle _spawnlp – _spawnlpe – _spawnv _spawnve – _spawnvp _spawnvpe _wspawnl – _wspawnle – _wspawnlp – _wspawnlpe – _ wspawnv – _wspawnve – _wspawnvp – _wspawnvpe – _wsystem – execl – execle – execlp – execlpe – execv – execve – execvp – execvpe – spawnl – spawnle – spawnlp – spawnlpe – spawnv – spawnve – spawnvp – spawnvpe – systém|Funkce není k dispozici v aplikacích pro UPW. Aplikace pro UPW nelze volat jiné aplikace pro UPW nebo desktopové aplikace.|Alternativní řešení neexistuje.|
|_heapwalk _heapadd – _heapchk – _heapset – _heapused|Tyto funkce se obvykle používají pro práci s haldy. Nicméně odpovídající rozhraní Win32 API nejsou podporovány v aplikacích pro UWP. A aplikace už můžete vytvořit nebo použít privátní haldy.|Alternativní řešení neexistuje. Nicméně `_heapwalk` k dispozici v ladění CRT pouze pro účely ladění. Tyto nelze použít v aplikacích, které se nahrají do Microsoft Store.|

Následující funkce jsou k dispozici v CRT pro aplikace pro UPW, ale dá se použít jenom v případě odpovídající Win32 nebo rozhraní API Windows Runtime nelze použít – například když provádíte přenos rozsáhlých základů kódu

|||
|-|-|
|Funkce jednobajtového řetězce – například `strcat`, `strcpy`, `strlwr`, a tak dále.|Vytvářejte aplikace pro UPW výhradně kódování Unicode vzhledem k tomu, že všechna rozhraní Win32 API a rozhraní API Windows Runtime, která jsou přístupné pomocí znakové sady pouze kódování Unicode.  Jednobajtové funkce byly zanechány přenášíte velké kód bází, ale mělo by se jinak vyhnout, a odpovídající funkce širokých by místo toho použít, pokud je to možné.|
|Stream vstup/výstup a funkce pro vstupně-výstupních operací nízké úrovně souboru – například `fopen`, `open`, a tak dále.|Tyto funkce jsou synchronní, což se nedoporučuje pro aplikace pro UPW. V aplikacích pro UWP pomocí asynchronní rozhraní API můžete otevřít, číst z a zápis do souborů k zabránění blokování vlákna uživatelského rozhraní. Příkladem takových rozhraní API jsou ty, které v `Windows::Storage::FileIO` třídy.|

## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Aplikace Windows 8.x Store a Windows Phone 8.x aplikace

Kromě výše uvedených rozhraní API nejsou k dispozici v aplikacích Windows Phone 8.x a Windows 8.x Store aplikace následující rozhraní API.

||||
|-|-|-|
|_beginthread _beginthreadex _endthread _endthreadex|Dělení na vlákna rozhraní Win32 API nejsou k dispozici v aplikacích pro Windows 8.x Store.|Použití `Windows Runtime Windows::System::Threading::ThreadPool` nebo `concurrency::task` místo.|
|_chdir _wchdir _getcwd _getdcwd _wgetcwd _wgetdcwd|Koncept pracovního adresáře neplatí pro aplikace Windows 8.x Store.|Místo toho používejte úplné cesty.|
|_getpid|Tato funkce se v předchozích verzích CRT zastaralé.|Použití rozhraní API systému Win32 `GetCurrentProcessId()`|
|_isleadbyte_l _ismbbalnum, _ismbbalnum_l, _ismbbalpha, _ismbbalpha _ismbbalpha_l _ismbbgraph _ismbbgraph_l _ismbbkalnum _ismbbkalnum_l _ismbbkana _ismbbkana_l _ismbbkprint _ismbbkprint_l _ismbbkpunct _ismbbkpunct_l _ismbblead _ismbblead_l _ismbbprint _ismbbprint_l _ismbbpunct _ismbbpunct_l _ismbbtrail _ismbbtrail_l _ismbslead _ismbslead_l _ismbstrail _ismbstrail_l _mbsdup isleadbyte|Vícebajtové řetězce nejsou podporovány v aplikacích pro Windows 8.x Store.|Místo toho použijte řetězců v kódu Unicode.|
|_tzset|Proměnné prostředí nejsou k dispozici pro Windows 8.x Store aplikace.|Alternativní řešení neexistuje.|
|_get_heap_handle – _heapmin –|Odpovídající rozhraní Win32 API nejsou podporovány v aplikacích pro Windows 8.x Store. A aplikace již nelze vytvářet privátní haldy.|Alternativní řešení neexistuje. Nicméně `_get_heap_handle` je k dispozici v ladění CRT pouze pro účely ladění.|