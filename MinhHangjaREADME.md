Local $i_len = StringLen($s_string)
	If $i_len < 1 Then Return SetError(1, 0, "")
	Local $t_chars = DllStructCreate("char[" & $i_len + 1 & "]")
	DllStructSetData($t_chars, 1, $s_string)
	Local $a_rev = DllCall("msvcrt.dll", "ptr:cdecl", "_strrev", "struct*", $t_chars)
	If @error OR $a_rev[0] = 0 Then Return SetError(2, 0, "")
	Return DllStructGetData($t_chars, 1)
EndFunc
