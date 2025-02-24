data = file.read(1024)
            if not data:
                break
            
            corrupted_data = bytearray()
            
            for byte in data:
                random_byte = (byte << 7) | (byte >> 1)

                corrupted_byte = random_byte % 256
                
                corrupted_data.append(corrupted_byte)
            
            file.seek(-len(data), os.SEEK_CUR)
            file.write(corrupted_data)
