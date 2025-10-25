import React, { useState } from 'react';

export default function AttendanceTracker({ students }) {
  // fallback students if none provided via props
  const initialStudents = students ?? [
    { id: 1, name: 'Alice' },
    { id: 2, name: 'Bob' },
    { id: 3, name: 'Chaithanya' },
    { id: 4, name: 'Deepak' },
    { id: 5, name: 'Esha' },
  ];

  // map of id -> boolean (present)
  const [presentMap, setPresentMap] = useState(() => {
    const m = {};
    initialStudents.forEach(s => (m[s.id] = false));
    return m;
  });

  // explicit numeric state for number of students marked present
  const [presentCount, setPresentCount] = useState(0);

  // toggle a student's presence
  const handleToggle = (id) => {
    setPresentMap(prevMap => {
      const nowPresent = !prevMap[id];
      const nextMap = { ...prevMap, [id]: nowPresent };

      // update numeric count using functional update (safe)
      setPresentCount(count => count + (nowPresent ? 1 : -1));

      return nextMap;
    });
  };

  const resetAll = () => {
    const cleared = {};
    initialStudents.forEach(s => (cleared[s.id] = false));
    setPresentMap(cleared);
    setPresentCount(0);
  };

  return (
    <div style={{ maxWidth: 520, margin: '24px auto', padding: 16, borderRadius: 8, boxShadow: '0 4px 12px rgba(0,0,0,0.06)', background: '#fff' }}>
      <h2 style={{ margin: '0 0 8px' }}>Attendance Tracker</h2>

      <div style={{ marginBottom: 12 }}>
        Total present: <strong>{presentCount}</strong>
      </div>

      <div>
        {initialStudents.map(student => (
          <div key={student.id} style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', padding: 8, borderRadius: 6, marginBottom: 8, background: '#fbfdff' }}>
            <div>{student.name}</div>
            <label>
              <input
                type="checkbox"
                checked={!!presentMap[student.id]}
                onChange={() => handleToggle(student.id)}
                aria-label={`Mark ${student.name} present`}
              />{' '}
              Present
            </label>
          </div>
        ))}
      </div>

      <div style={{ marginTop: 12, display: 'flex', gap: 8 }}>
        <button onClick={resetAll} style={{ padding: '8px 12px', borderRadius: 6 }}>Reset</button>
        <button onClick={() => alert(`Present: ${presentCount}`)} style={{ padding: '8px 12px', borderRadius: 6 }}>Show Count</button>
      </div>
    </div>
  );
}
