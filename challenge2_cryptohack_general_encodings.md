ENCODING CHALLENGES
1)ASCII

          nums = [99, 114, 121, 112, 116, 111, 123, 65, 83, 67, 73, 73, 95, 112, 114, 49, 110, 116, 52, 98, 108, 51, 125]
        print("".join(chr(n) for n in nums))
        output :crypto{ASCII_pr1nt4bl3}

2)HEX

    bytes.fromhex("63727970746f7b596f755f77696c6c5f62655f776f726b696e675f776974685f6865785f737472696e67735f615f6c6f747d").decode()
    output:crypto{You_will_be_working_with_hex_strings_a_lot}


3)BASE64

    import base64
    hex_str = "72bca9b68fc16ac7beeb8f849dca1d8a783e8acf9679bf9269f7bf"
    bytes_data = bytes.fromhex(hex_str)
    b64 = base64.b64encode(bytes_data)
    print(b64.decode())
    output:crypto/Base+64+Encoding+is+Web+Safe/


4)BYTES AND BIG INTEGERS

    
      base10 = 11515195063862318899931685488813747395775516287289682636499965282714637259206269  # Given number
      # Step 1: Convert base-10 → hex string
      hex_str = hex(base10)[2:]  # remove '0x' prefix
      if len(hex_str) % 2 == 1:
          hex_str = '0' + hex_str  # pad with zero if needed
      print("Hex string:", hex_str)
      
      # Step 2: Convert hex string → bytes
      byte_data = bytes.fromhex(hex_str)
      print("Bytes:", byte_data)
      
      # Step 3: Convert bytes → ASCII string
      message = byte_data.decode()
      print("Message:", message)

  

      output:Hex string: 63727970746f7b336e633064316e365f346c6c5f3768335f7734795f6430776e7d
            Bytes: b'crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}'
           Message: crypto{3nc0d1n6_4ll_7h3_w4y_d0wn}
