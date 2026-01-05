<div style="overflow-x:auto;">
  <table style="width:100%; border-collapse: collapse; border: 1px solid #ccc;">
    <thead>
      <tr style="background-color: #f4f6f8; text-align: left;">
        <th style="padding: 10px; border: 1px solid #ccc;">Field</th>
        <th style="padding: 10px; border: 1px solid #ccc;">IPv4 (20 bytes minimum)</th>
        <th style="padding: 10px; border: 1px solid #ccc;">IPv6 (40 bytes fixed)</th>
        <th style="padding: 10px; border: 1px solid #ccc;">Key Differences / Notes</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Version</td>
        <td style="padding: 10px; border: 1px solid #ccc;">4 bits (always 4)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">4 bits (always 6)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Identifies protocol version</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Header Length (IHL)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">4 bits (in 32-bit words)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Fixed 40 bytes (no variable header length)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">IPv6 removes variable header → faster processing</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Type of Service / Traffic Class</td>
        <td style="padding: 10px; border: 1px solid #ccc;">8 bits (ToS / DSCP + ECN)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">8 bits (Traffic Class) + 20-bit Flow Label</td>
        <td style="padding: 10px; border: 1px solid #ccc;">IPv6 adds Flow Label for better QoS / flow handling</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Total Length</td>
        <td style="padding: 10px; border: 1px solid #ccc;">16 bits (max 65,535 bytes)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">16 bits (Payload Length)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">IPv6 = length of payload only (header is fixed)</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Identification</td>
        <td style="padding: 10px; border: 1px solid #ccc;">16 bits</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Removed</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Fragmentation moved to extension headers</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Flags</td>
        <td style="padding: 10px; border: 1px solid #ccc;">3 bits (DF, MF)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Removed</td>
        <td style="padding: 10px; border: 1px solid #ccc;">—</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Fragment Offset</td>
        <td style="padding: 10px; border: 1px solid #ccc;">13 bits</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Removed</td>
        <td style="padding: 10px; border: 1px solid #ccc;">—</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Time to Live (TTL)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">8 bits</td>
        <td style="padding: 10px; border: 1px solid #ccc;">8 bits (Hop Limit)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Same purpose, renamed for clarity</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Protocol / Next Header</td>
        <td style="padding: 10px; border: 1px solid #ccc;">8 bits (TCP=6, UDP=17, etc.)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">8 bits (Next Header)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Points to next header (can be extension header)</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Header Checksum</td>
        <td style="padding: 10px; border: 1px solid #ccc;">16 bits</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Removed</td>
        <td style="padding: 10px; border: 1px solid #ccc;">No checksum → faster, upper layers handle it</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Source Address</td>
        <td style="padding: 10px; border: 1px solid #ccc;">32 bits</td>
        <td style="padding: 10px; border: 1px solid #ccc;">128 bits</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Main change – much larger address</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Destination Address</td>
        <td style="padding: 10px; border: 1px solid #ccc;">32 bits</td>
        <td style="padding: 10px; border: 1px solid #ccc;">128 bits</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Main change – much larger address</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Options</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Variable length (up to 40 bytes)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Removed (moved to Extension Headers)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">IPv6 uses optional extension headers instead</td>
      </tr>
      <tr>
        <td style="padding: 10px; border: 1px solid #ccc;">Padding</td>
        <td style="padding: 10px; border: 1px solid #ccc;">Yes (to 32-bit boundary)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">No (fixed length)</td>
        <td style="padding: 10px; border: 1px solid #ccc;">—</td>
      </tr>
    </tbody>
  </table>
</div>
