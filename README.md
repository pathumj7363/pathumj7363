import React from "react";
import { Card, CardContent } from "@/components/ui/card";
import { PieChart, Pie, Cell, Tooltip, Legend } from "recharts";
import { motion } from "framer-motion";

const data = [
  { name: "JavaScript", value: 40 },
  { name: "Python", value: 25 },
  { name: "Java", value: 15 },
  { name: "C++", value: 10 },
  { name: "Other", value: 10 },
];

const COLORS = ["#0088FE", "#00C49F", "#FFBB28", "#FF8042", "#AA66CC"];

export default function ProfileDashboard() {
  return (
    <div className="grid grid-cols-1 md:grid-cols-2 gap-6 p-6">
      {/* LinkedIn + GitHub Info */}
      <motion.div
        initial={{ opacity: 0, y: 20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.6 }}
      >
        <Card className="rounded-2xl shadow-lg p-4">
          <CardContent>
            <h2 className="text-xl font-bold mb-2">🌐 LinkedIn</h2>
            <p className="text-base mb-4">
              <a
                href="https://www.linkedin.com/in/pathum-jayasiri-10a905337/"
                target="_blank"
                className="text-blue-600 underline"
              >
                linkedin.com/in/pathum-jayasiri-10a905337
              </a>
            </p>

            <h2 className="text-xl font-bold mb-2">💻 GitHub</h2>
            <p className="text-base">
              <a
                href="https://github.com/your-github-username"
                target="_blank"
                className="text-gray-800 underline"
              >
                github.com/your-github-username
              </a>
            </p>
          </CardContent>
        </Card>
      </motion.div>

      {/* GitHub Analytics Pie Chart */}
      <motion.div
        initial={{ opacity: 0, y: 20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.6, delay: 0.2 }}
      >
        <Card className="rounded-2xl shadow-lg p-4 flex flex-col items-center">
          <h2 className="text-xl font-bold mb-4">📊 GitHub Language Distribution</h2>
          <PieChart width={300} height={300}>
            <Pie
              data={data}
              cx="50%"
              cy="50%"
              innerRadius={60}
              outerRadius={100}
              paddingAngle={5}
              dataKey="value"
            >
              {data.map((entry, index) => (
                <Cell key={`cell-${index}`} fill={COLORS[index % COLORS.length]} />
              ))}
            </Pie>
            <Tooltip />
            <Legend />
          </PieChart>
        </Card>
      </motion.div>
    </div>
  );
}
