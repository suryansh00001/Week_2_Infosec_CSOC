We're given 2 files ... one was base64 text and another is output.txt
on decoding the base64 text we got 


    with open('flag.txt', 'r') as f :
       flag = f.read()
    
    s = ''.join(format(ord(i), '02x') for i in flag)
    e = ""
    
    for i in range(0,len(s),4) :
       e += format(int(s[i:i+2],16), '02x')+format(int(s[i:i+2],16)^int(s[i+2:i+4],16), '02x')
    
    with open('output.txt', 'w') as f :
       f.write(e)

basically it is encrypting our flag
to decrypt we have to reverse this

so here's the reverse code


    with open('output.txt', 'r') as f:
        e = f.read().strip()
    
    flag = ""
    for i in range(0, len(e), 4):
        a = int(e[i:i+2], 16)
        ab = int(e[i+2:i+4], 16)
        b = a ^ ab
        flag += chr(a) + chr(b)
    
    print("Recovered flag:", flag)
we got the flag

    CSOC25{Cus70m_3nc0d1n9_X0r_rul3z!}


