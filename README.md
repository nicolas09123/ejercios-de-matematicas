import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

export default function CarBuilderApp() {
  const [body, setBody] = useState("sport");
  const [wheels, setWheels] = useState("classic");
  const [color, setColor] = useState("#ff0000");

  const bodies = ["sport", "sedan", "truck"];
  const wheelTypes = ["classic", "racing", "offroad"];

  const bodyImages = {
    sport: "/images/bodies/sport.png",
    sedan: "/images/bodies/sedan.png",
    truck: "/images/bodies/truck.png",
  };

  const wheelImages = {
    classic: "/images/wheels/classic.png",
    racing: "/images/wheels/racing.png",
    offroad: "/images/wheels/offroad.png",
  };

  return (
    <div className="p-4 max-w-4xl mx-auto space-y-6">
      <h1 className="text-3xl font-bold text-center">🛠 Arma tu carro</h1>

      <Card>
        <CardContent className="p-4 space-y-4">
          <div>
            <label className="font-semibold">Carrocería:</label>
            <div className="flex space-x-2 mt-2">
              {bodies.map((b) => (
                <Button
                  key={b}
                  variant={b === body ? "default" : "outline"}
                  onClick={() => setBody(b)}
                >
                  {b}
                </Button>
              ))}
            </div>
          </div>

          <div>
            <label className="font-semibold">Ruedas:</label>
            <div className="flex space-x-2 mt-2">
              {wheelTypes.map((w) => (
                <Button
                  key={w}
                  variant={w === wheels ? "default" : "outline"}
                  onClick={() => setWheels(w)}
                >
                  {w}
                </Button>
              ))}
            </div>
          </div>

          <div>
            <label className="font-semibold">Color del carro:</label>
            <input
              type="color"
              value={color}
              onChange={(e) => setColor(e.target.value)}
              className="ml-2"
            />
          </div>
        </CardContent>
      </Card>

      <Card>
        <CardContent className="p-6 flex justify-center items-center">
          <div className="relative w-[300px] h-[150px]">
            <div
              className="absolute top-0 left-0 w-full h-full rounded-xl"
              style={{ backgroundColor: color }}
            ></div>
            <img
              src={bodyImages[body]}
              alt="Car body"
              className="absolute top-0 left-0 w-full h-full opacity-90"
            />
            <img
              src={wheelImages[wheels]}
              alt="Wheels"
              className="absolute bottom-0 left-0 w-full h-1/3"
            />
          </div>
        </CardContent>
      </Card>
    </div>
  );
}
